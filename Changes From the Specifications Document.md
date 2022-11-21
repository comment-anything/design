

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
Changed `server.FeedbackRecord.type` to `server.FeedbackRecord.feedbackType`


# Caching Entities

Changed `CachedComment`, added fields `id` and `content`
Changed `Page.comments` from type `[]Cachedcomment` to `Map<int64, CachedComment>`


# Database

Changed all instances of `user` to `user_id` ; in PostgresSQL, `user` is a reserved keyword!

Changed `DomainModerators` table to `DomainModeratorAssignments`, added "ID" and "is_deactivation" fields.
Changed `GlobalModerators` table to `GlobalModeratorAssignments`, added "ID" and "is_deactivation" fields.
Changed `Admins` table to `AdminAssignments`
Changed `VoteRecord` `VoteRecords`, changed `VoteRecord`.`commentId` to `comment_id`.
Changed `Reports` to `CommentReports`, added fk to comment (oversight)


