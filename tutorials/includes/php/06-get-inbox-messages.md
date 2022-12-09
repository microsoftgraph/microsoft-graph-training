---
ms.localizationpriority: medium
---

<!-- markdownlint-disable MD041 -->

In this section you will add the ability to list messages in the user's email inbox.

1. Add the following code to the `GraphHelper` class.

    :::code language="php" source="./src/user-auth/graphtutorial/GraphHelper.php" id="GetInboxSnippet":::

1. Replace the empty `listInbox` function in **main.php** with the following.

    :::code language="php" source="./src/user-auth/graphtutorial/main.php" id="ListInboxSnippet":::

1. Run the app, sign in, and choose option 2 to list your inbox.

    ```bash
    Please choose one of the following options:
    0. Exit
    1. Display access token
    2. List my inbox
    3. Send mail
    4. Make a Graph call
    2
    Message: Updates from Ask HR and other communities
      From: Contoso Demo on Yammer
      Status: Read
      Received: Mon, 18 Apr 2022 14:24:16 +0000
    Message: Employee Initiative Thoughts
      From: Patti Fernandez
      Status: Read
      Received: Mon, 18 Apr 2022 13:52:03 +0000
    Message: Voice Mail (11 seconds)
      From: Alex Wilber
      Status: Unread
      Received: Wed, 13 Apr 2022 02:30:27 +0000
    Message: Our Spring Blog Update
      From: Alex Wilber
      Status: Unread
      Received: Tue, 12 Apr 2022 16:46:01 +0000
    Message: Atlanta Flight Reservation
      From: Alex Wilber
      Status: Unread
      Received: Mon, 11 Apr 2022 13:39:10 +0000
    Message: Atlanta Trip Itinerary - down time
      From: Alex Wilber
      Status: Unread
      Received: Fri, 08 Apr 2022 18:36:01 +0000

    ...

    More messages available? True
    ```

## Code explained

Consider the code in the `getInbox` function.

### Accessing well-known mail folders

The function passes `/me/mailFolders/inbox/messages` to the request builder, which builds a request to the [List messages](/graph/api/user-list-messages) API. Because it includes the `/mailFolders/inbox` segment, the API will only return messages in the requested mail folder. In this case, because the inbox is a default, well-known folder inside a user's mailbox, it's accessible via its well-known name. Non-default folders are accessed the same way, by replacing the well-known name with the mail folder's ID property. For details on the available well-known folder names, see [mailFolder resource type](/graph/api/resources/mailfolder).

### Accessing a collection

Unlike the `getUser` function from the previous section, which returns a single object, this method returns a collection of messages. Most APIs in Microsoft Graph that return a collection do not return all available results in a single response. Instead, they use [paging](/graph/paging) to return a portion of the results while providing a method for clients to request the next "page".

#### Default page sizes

APIs that use paging implement a default page size. For messages, the default value is 10. Clients can request more (or less) by using the [$top](/graph/query-parameters#top-parameter) query parameter. In `getInbox`, this is accomplished with the `setPageSize` method on the request builder.

> [!NOTE]
> The value passed in `setPageSize` is an upper-bound, not an explicit number. The API returns a number of messages *up to* the specified value.

#### Getting subsequent pages

If there are more results available on the server, collection responses include an `@odata.nextLink` property with an API URL to access the next page. The PHP SDK exposes this as the `isEnd` method on collection request objects. If this method returns false, there are more results available. The next page can be accessed by the `getPage` method.

### Sorting collections

The function uses the [$orderby query parameter](/graph/query-parameters#orderby-parameter) to request results sorted by the time the message is received (`receivedDateTime` property). It includes the `DESC` keyword so that messages received more recently are listed first.
