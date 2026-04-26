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
