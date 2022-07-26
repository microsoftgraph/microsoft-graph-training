---
ms.localizationpriority: medium
---

<!-- markdownlint-disable MD041 -->

In this section you will add the ability to list messages in the user's email inbox.

1. Open **graphHelper.js** and add the following function.

    :::code language="javascript" source="./src/demo/graphtutorial/graphHelper.js" id="GetInboxSnippet":::

1. Replace the empty `ListInboxAsync` function in **index.js** with the following.

    :::code language="javascript" source="./src/demo/graphtutorial/index.js" id="ListInboxSnippet":::

1. Run the app, sign in, and choose option 2 to list your inbox.

    ```bash
    [1] Display access token
    [2] List my inbox
    [3] Send mail
    [4] List users (requires app-only)
    [5] Make a Graph call
    [0] Exit

    Select an option [1...5 / 0]: 2
    Message: Updates from Ask HR and other communities
      From: Contoso Demo on Yammer
      Status: Read
      Received: 12/30/2021 4:54:54 AM -05:00
    Message: Employee Initiative Thoughts
      From: Patti Fernandez
      Status: Read
      Received: 12/28/2021 5:01:10 PM -05:00
    Message: Voice Mail (11 seconds)
      From: Alex Wilber
      Status: Unread
      Received: 12/28/2021 5:00:46 PM -05:00
    Message: Our Spring Blog Update
      From: Alex Wilber
      Status: Unread
      Received: 12/28/2021 4:49:46 PM -05:00
    Message: Atlanta Flight Reservation
      From: Alex Wilber
      Status: Unread
      Received: 12/28/2021 4:35:42 PM -05:00
    Message: Atlanta Trip Itinerary - down time
      From: Alex Wilber
      Status: Unread
      Received: 12/28/2021 4:22:04 PM -05:00

    ...

    More messages available? true
    ```

## Code explained

Consider the code in the `getInboxAsync` function.

### Accessing well-known mail folders

The function passes `/me/mailFolders/inbox/messages` to the `_userClient.api` request builder, which builds a request to the [List messages](/graph/api/user-list-messages) API. Because it includes the `/mailFolders/inbox` portion of the API endpoint, the API will only return messages in the requested mail folder. In this case, because the inbox is a default, well-known folder inside a user's mailbox, it's accessible via its well-known name. Non-default folders are accessed the same way, by replacing the well-known name with the mail folder's ID property. For details on the available well-known folder names, see [mailFolder resource type](/graph/api/resources/mailfolder).

### Accessing a collection

Unlike the `getUserAsync` function from the previous section, which returns a single object, this method returns a collection of messages. Most APIs in Microsoft Graph that return a collection do not return all available results in a single response. Instead, they use [paging](/graph/paging) to return a portion of the results while providing a method for clients to request the next "page".

#### Default page sizes

APIs that use paging implement a default page size. For messages, the default value is 10. Clients can request more (or less) by using the [$top](/graph/query-parameters#top-parameter) query parameter. In `getInboxAsync`, this is accomplished with the `.top(25)` method.

> [!NOTE]
> The value passed to `.top()` is an upper-bound, not an explicit number. The API returns a number of messages *up to* the specified value.

#### Getting subsequent pages

If there are more results available on the server, collection responses include an `@odata.nextLink` property with an API URL to access the next page. The JavaScript client library exposes this property on `PageCollection` objects. If this property is not undefined, there are more results available.

The value of `@odata.nextLink` can be passed to `_userClient.api` to get the next page of results. Alternatively, you can use the `PageIterator` object from the client library to [iterate over all available pages](/graph/sdks/paging).

### Sorting collections

The function uses the `orderby` method on the request to request results sorted by the time the message is received (`receivedDateTime` property). It includes the `DESC` keyword so that messages received more recently are listed first. This adds the [$orderby query parameter](/graph/query-parameters#orderby-parameter) to the API call.
