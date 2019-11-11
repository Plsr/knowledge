# Active Storage
Active Storage is a way to handle file uploads at ease that was introduced in Rails 5. It makes uploading and processing files in your rails applications reallystraight forward.

### Resize and crop an avatar image to a square

```ruby
image_tag user.avatar.variant(combine_options: {resize: '256x256^', extent: '256x256', gravity: 'Center'})
```

[Source](https://grosse.io/blog/posts/ActiveStorage-avatar-image-with-resize-crop)
