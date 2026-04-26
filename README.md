## Sample Front-end using React.js

### Database
this is a sample DB

```==> Database```
```Javascript
CREATE TABLE IF NOT EXISTS work (
  id SERIAL PRIMARY KEY,
  name VARCHAR(255),
  position VARCHAR(150),
  github TEXT,
  demo TEXT,
  framework VARCHAR(255),
  description TEXT,
  created_at TIMESTAMP DEFAULT NOW()
);

CREATE TABLE IF NOT EXISTS image_work (
  id SERIAL PRIMARY KEY,
  originalname VARCHAR(255) NOT NULL,
  path TEXT NOT NULL,
  filename VARCHAR(255) NOT NULL,
  size INT NOT NULL,
  encoding VARCHAR(255) NOT NULL,
  by_work INT NOT NULL,
  created_at TIMESTAMP DEFAULT NOW(),
  CONSTRAINT fk_image_work
    FOREIGN KEY (by_work) REFERENCES work(id)
    ON DELETE CASCADE
);
```
### 1. Prepare requests in React
#### 1. Data of work
```==> Input form work```
```Javascript 
<form onSubmit={handleSubmit}>
  <div>
    <label>Name:</label>
    <input type="text" name="name" value={form.name}
      onChange={handleChange}
      required
    />
  </div>
  <div>
    <label>Position:</label>
    <input
      type="text" name="position" value={form.position}
      onChange={handleChange}
    />
  </div>
  <div>
    <label>GitHub:</label>
    <input type="text" name="github" value={form.github}
      onChange={handleChange}
    />
  </div>
  // ... demo, framework, description
  <br />
  <button type="submit">Submit</button>
</form>
```
```==> Form work using useState```
```Javascript 
const [form, setForm] = useState({
  name: "",
  position: "",
  framework: "",
  github: "",
  demo: "",
  description: "",
});
```
```==> Handle onChange function```
```Javascript 
const handleOnChange = (e) => {
  const { name, value } = e.target;
  setForm((prev) => ({
    ...prev,
    [name]: value,
  }));
};
```
#### 2. Image of work
```==> Input image form work```
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
```==> Form work using useState```
```Javascript 
const [images, setImages] = useState([]);
const [preview, setPreview] = useState([]);
```
```==> Handle onChange function```
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
