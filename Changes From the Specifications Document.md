

The purpose of this document is to record all changes we make from the design described in the Specifications document. All changes to Specs need to be described in Design.



# States

Added `LoggedOut: ViewUserProfile`, `LoggedIn: Member: ViewUserProfile`, `LoggedIn: Moderator: ViewUserProfile`, `LoggedIn: Admin: ViewUserProfile`

# Client-Server Communication Entities

Changed `client.GetComments.sortOrder` to `client.GetComments.SortAscending` and changed type from `int8` to `bool` 
Changed `client.Feedback.type` to `client.Feedback.FeedbackType`
Changed `client.ViewFeedback.type` to `client.Feedback.FeedbackType`
Changed `client.getUserProfile` to `client.GetUserProfile`
Changed `client.ViewBans.forDomains` from type `string` to type `string[]`
Changed `client.ViewMods.forDomains` from type `string` to type `string[]`

Added `client.AssignGlobalModerator`
Added `client.AssignDomainModerator`

Added `client.ViewDomainReport`
Added `client.ViewUsersReport`

Added `server.Message`

Changed `client.RequestValidation` to `client.RequestVerification`
Changed `client.Validate` to `client.Verify`

Added `client.ViewLogs.StartingAt` and `client.ViewLogs.EndingAt`

Capitalized the first letter of all fields in `client` structs for golang exporting


# Server-Client Communication Entities

Changed `server.Comment`, added field `UserId`
Changed `server.CommentVote` to `Server.CommentVoteDimension`
Changed `server.UserProfile.DomainsModerating` type from `string` to `string[]`
Changed `server.FeedbackRecord.type` to `server.FeedbackRecord.FeedbackType`

Added fields `BannedByUserID`, `BannedByUsername`, `BannedAt`, `BanReason` to `client.BanRecord`

Added `server.LogoutResponse`

Capitalized all fields.

# Caching Entities

Changed `CachedComment`, added fields `id` and `content`
Changed `Page.comments` from type `[]Cachedcomment` to `Map<int64, CachedComment>`


# Database

Changed all instances of `user` to `user_id` ; in PostgresSQL, `user` is a reserved keyword!

Changed `DomainModerators` table to `DomainModeratorAssignments`, added "ID" and "is_deactivation" fields.
Changed `GlobalModerators` table to `GlobalModeratorAssignments`, added "ID" and "is_deactivation" fields.
Changed `Admins` table to `AdminAssignments`, added field `assigned_at`
Changed `VoteRecord` `VoteRecords`, changed `VoteRecord`.`commentId` to `comment_id`.
Changed `Reports` to `CommentReports`, added fk to comment (oversight)
Changed `CommentModerationActions.CommentId` to `CommentModerationActions.comment_id`.
Changed `Logs.user` to `Logs.user_id`
Added `Logs.at_time` field to track time log was made.

Changed table `ValidationCodes` to `VerificationCodes`


