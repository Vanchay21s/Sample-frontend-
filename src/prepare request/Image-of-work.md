#### Image of work
```1. Input image form work```
```Javascript 
<div>
  <label>Upload Images:</label>
  <input
    type="file"
    multiple
    accept="image/*"
    onChange={handleImageChange}
  />
</div>
{/* Preview */}
<div style={{ display: "flex", gap: "10px", marginTop: "10px" }}>
  {preview.map((src, index) => (
    <img
      key={index}
      src={src}
      alt="preview"
      width="100"
      height="100"
      style={{ objectFit: "cover" }}
    />
  ))}
</div>
```

```2. Form work using useState```
```Javascript 
const [images, setImages] = useState([]);
const [preview, setPreview] = useState([]);
```

```3. Handle onChange function```
```Javascript 
const handleImageChange = (e) => {
  const files = Array.from(e.target.files);
  setImages(files);

  // preview images
  const previewUrls = files.map((file) =>
    URL.createObjectURL(file)
  );
  setPreview(previewUrls);
};
```
