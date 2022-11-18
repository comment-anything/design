

The purpose of this document is to record all changes we make from the design described in the Specifications document. All changes to Specs need to be described in Design.





# Client-Server Communication Entities

Changed `client.GetComments.sortOrder` to `client.GetComments.SortAscending` and changed type from `int8` to `bool` 
Changed `client.Feedback.type` to `client.Feedback.FeedbackType`
Changed `client.ViewFeedback.type` to `client.Feedback.FeedbackType`
Changed `client.getUserProfile` to `client.GetUserProfile`
Changed `client.ViewBans.forDomains` from type `string` to type `string[]`
Changed `client.ViewMods.forDomains` from type `string` to type `string[]`

Capitalized the first letter of all fields in `client` structs for golang exporting


# Server-Client Communication Entities

Changed `server.Comment`, added field `userId`
Changed `server.CommentVote` to `Server.CommentVoteDimension`
Changed `server.UserProfile.DomainsModerating` type from `string` to `string[]`