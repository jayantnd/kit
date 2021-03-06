
# session
    import "github.com/ardanlabs/kit/auth/session"

Package session provides a level of security for web tokens by giving them an
expiration date and a lookup point for the user accessing the API. The session
is what is used to look up the user performing the web call. Though the user's
PublicID is not private, it is not used directly.




## Constants
``` go
const Collection = "auth_sessions"
```
Collection contains the name of the user collection.




## type Session
``` go
type Session struct {
    ID          bson.ObjectId `bson:"_id,omitempty" json:"_id,omitempty"`
    SessionID   string        `bson:"session_id" json:"session_id"`
    PublicID    string        `bson:"public_id" json:"public_id"`
    DateExpires time.Time     `bson:"date_expires" json:"date_expires"`
    DateCreated time.Time     `bson:"date_created" json:"date_created"`
}
```
Session denotes a user's session within the system.









### func Create
``` go
func Create(context interface{}, db *db.DB, publicID string, expires time.Duration) (*Session, error)
```
Create adds a new session for the specified user to the database.


### func GetByLatest
``` go
func GetByLatest(context interface{}, db *db.DB, publicID string) (*Session, error)
```
GetByLatest retrieves the latest session for the specified user.


### func GetBySessionID
``` go
func GetBySessionID(context interface{}, db *db.DB, sessionID string) (*Session, error)
```
GetBySessionID retrieves a session from the session store.




### func (\*Session) IsExpired
``` go
func (s *Session) IsExpired(context interface{}) bool
```
IsExpired returns true if the session is expired.









- - -
Generated by [godoc2md](http://godoc.org/github.com/davecheney/godoc2md)