android-AquaModel
=================

Built on top of

* Gson
* Volley
* Retrofit
* EventBus
* ObservableList

Model
===

```java
class Album extends AquaModel {
  @Identifier public string id;
  @Presence @ShorterThan(256) public String title;
  
  @BeforeSave
  private void beforeSave { .. }
}

interface AlbumService {
  @GET("/albums/{id}")
  List<Album> listAlbums(@Path("id") String id);
}
```

Requestable
---

```java
Album.list();
Album.fetch(3);
album.fetch();
album.push();
```

And will post an event via EventBus!

Validatable
---

```java
album.validate();
```

Serializable
---

```java
album.toJson();
Album.create(hash);
```

Callbackable
---

```java
album.save();
// will invoke album.beforeSave();
```
