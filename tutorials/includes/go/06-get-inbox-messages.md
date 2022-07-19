---
ms.localizationpriority: medium
---

<!-- markdownlint-disable MD041 -->

In this section you will add the ability to list messages in the user's email inbox.

[!INCLUDE [preview-disclaimer](preview-disclaimer.md)]

1. Add the following function to **./graphhelper/graphhelper.go**.

    :::code language="go" source="./src/demo/graphtutorial/graphhelper/graphhelper.go" id="GetInboxSnippet":::

1. Replace the empty `listInbox` function in **graphtutorial.go** with the following.

    :::code language="go" source="./src/demo/graphtutorial/graphtutorial.go" id="ListInboxSnippet":::

1. Run the app, sign in, and choose option 2 to list your inbox.

    ```bash
    Please choose one of the following options:
    0. Exit
    1. Display access token
    2. List my inbox
    3. Send mail
    4. List users (requires app-only)
    5. Make a Graph call
    2
    Message: Updates from Ask HR and other communities
      From: Contoso Demo on Yammer
      Status: Read
      Received: 2021-12-30 04:54:54 -0500 EST
    Message: Employee Initiative Thoughts
      From: Patti Fernandez
      Status: Read
      Received: 2021-12-28 17:01:10 -0500 EST
    Message: Voice Mail (11 seconds)
      From: Alex Wilber
      Status: Unread
      Received: 2021-12-28 17:00:46 -0500 EST
    Message: Our Spring Blog Update
      From: Alex Wilber
      Status: Unread
      Received: 2021-12-28 16:49:46 -0500 EST
    Message: Atlanta Flight Reservation
      From: Alex Wilber
      Status: Unread
      Received: 2021-12-28 16:35:42 -0500 EST
    Message: Atlanta Trip Itinerary - down time
      From: Alex Wilber
      Status: Unread
      Received: 2021-12-28 16:22:04 -0500 EST

    ...

    More messages available? True
    ```

## Code explained

Consider the code in the `GetInbox` function.

### Accessing well-known mail folders

The function uses the `userClient.Me().MailFoldersById("inbox").Messages()` request builder, which builds a request to the [List messages](/graph/api/user-list-messages) API. Because it includes the `MailFoldersById("inbox")` request builder, the API will only return messages in the requested mail folder. In this case, because the inbox is a default, well-known folder inside a user's mailbox, it's accessible via its well-known name. Non-default folders are accessed the same way, by replacing the well-known name with the mail folder's ID property. For details on the available well-known folder names, see [mailFolder resource type](/graph/api/resources/mailfolder).

### Accessing a collection

Unlike the `GetUser` function from the previous section, which returns a single object, this method returns a collection of messages. Most APIs in Microsoft Graph that return a collection do not return all available results in a single response. Instead, they use [paging](/graph/paging) to return a portion of the results while providing a method for clients to request the next "page".

#### Default page sizes

APIs that use paging implement a default page size. For messages, the default value is 10. Clients can request more (or less) by using the [$top](/graph/query-parameters#top-parameter) query parameter. In `GetInbox`, this is accomplished with the `Top` property in the query parameters.

> [!NOTE]
> The value passed in `Top` is an upper-bound, not an explicit number. The API returns a number of messages *up to* the specified value.

#### Getting subsequent pages

If there are more results available on the server, collection responses include an `@odata.nextLink` property with an API URL to access the next page. The Go SDK exposes this as the `GetNextLink` method on collection page objects. If this method returns non-nil, there are more results available.

### Sorting collections

The function uses the `OrderBy` property in the query parameters to request results sorted by the time the message is received (`receivedDateTime` property). It includes the `DESC` keyword so that messages received more recently are listed first. This adds the [$orderby query parameter](/graph/query-parameters#orderby-parameter) to the API call.
