Below are **clear, practical, interview-ready React solutions** for all 5 complex form problems.
These feature **real business validations** (password strength, multi-step forms, dynamic fields, file upload rules, PAN/Aadhaar validation).
Perfect for **2+ years experience React interviews**.

---

# ======================================================

# ✅ **11. Sign-up Form with Complex Validation**

### Requirements:

* Strong password
* Email format
* Confirm password must match
* Mobile number validation (10 digits in India)
  ======================================================

---

## ⭐ Validation Logic

```js
const validate = (values) => {
  const errors = {};

  // Email
  if (!/\S+@\S+\.\S+/.test(values.email)) {
    errors.email = "Invalid email format";
  }

  // Password (1 uppercase, lowercase, number, special char)
  if (!/^(?=.*[A-Z])(?=.*[a-z])(?=.*\d)(?=.*[@$!%*])[A-Za-z\d@$!%*]{8,}$/
      .test(values.password)) {
    errors.password = "Password must be 8+ chars, include uppercase, number, special char";
  }

  // Confirm password
  if (values.password !== values.confirmPassword) {
    errors.confirmPassword = "Passwords do not match";
  }

  // Mobile number
  if (!/^[6-9]\d{9}$/.test(values.mobile)) {
    errors.mobile = "Enter a valid 10-digit Indian mobile number";
  }

  return errors;
};
```

---

## ⭐ Form Example

```jsx
function SignupForm() {
  const [values, setValues] = useState({
    email: "",
    password: "",
    confirmPassword: "",
    mobile: ""
  });
  const [errors, setErrors] = useState({});

  const handleSubmit = (e) => {
    e.preventDefault();
    const validation = validate(values);
    setErrors(validation);
    if (Object.keys(validation).length === 0) {
      alert("Form submitted!");
    }
  };

  return (
    <form onSubmit={handleSubmit}>
      <input placeholder="Email"
             onChange={(e)=> setValues({...values, email:e.target.value})}/>
      {errors.email && <p>{errors.email}</p>}

      <input placeholder="Password" type="password"
             onChange={(e)=> setValues({...values, password:e.target.value})}/>
      {errors.password && <p>{errors.password}</p>}

      <input placeholder="Confirm Password" type="password"
             onChange={(e)=> setValues({...values, confirmPassword:e.target.value})}/>
      {errors.confirmPassword && <p>{errors.confirmPassword}</p>}

      <input placeholder="Mobile Number"
             onChange={(e)=> setValues({...values, mobile:e.target.value})}/>
      {errors.mobile && <p>{errors.mobile}</p>}

      <button type="submit">Sign up</button>
    </form>
  );
}
```

---

### ✔ Explanation

* Uses regex for password strength
* Compares both passwords
* Validates email/mobiles properly
* Shows error messages dynamically

---

# ======================================================

# ✅ **12. Multi-Step Form (Stepper UI)**

### Steps:

1. Personal Data
2. Address
3. Review & Submit
   ======================================================

---

## ⭐ Stepper Logic

```jsx
const [step, setStep] = useState(1);
const next = () => setStep(s => s + 1);
const prev = () => setStep(s => s - 1);
```

---

## ⭐ Multi-Step Form UI

```jsx
function MultiStepForm() {
  const [data, setData] = useState({
    name: "",
    age: "",
    address: "",
    city: ""
  });

  return (
    <>
      <h2>Step {step}</h2>

      {step === 1 && (
        <>
          <input placeholder="Name"
                 onChange={(e)=> setData({...data, name:e.target.value})}/>
          <input placeholder="Age"
                 onChange={(e)=> setData({...data, age:e.target.value})}/>
          <button onClick={next}>Next</button>
        </>
      )}

      {step === 2 && (
        <>
          <input placeholder="Address"
                 onChange={(e)=> setData({...data, address:e.target.value})}/>
          <input placeholder="City"
                 onChange={(e)=> setData({...data, city:e.target.value})}/>
          <button onClick={prev}>Back</button>
          <button onClick={next}>Next</button>
        </>
      )}

      {step === 3 && (
        <>
          <pre>{JSON.stringify(data, null, 2)}</pre>
          <button onClick={prev}>Back</button>
          <button onClick={() => alert("Submitted!")}>Submit</button>
        </>
      )}
    </>
  );
}
```

---

### ✔ Explanation

* Uses one shared state object
* Step UI is conditionally displayed
* Stepper allows back/forward navigation
* Final step shows review before submission

---

# ======================================================

# ✅ **13. Dynamic Form Fields**

### Add/remove phone number fields dynamically

======================================================

---

## ⭐ Dynamic Inputs

```jsx
function PhoneForm() {
  const [phones, setPhones] = useState([""]);

  const addField = () => setPhones([...phones, ""]);
  const removeField = (i) => setPhones(phones.filter((_, idx) => idx !== i));

  const updateField = (value, i) =>
    setPhones(phones.map((p, idx) => (i === idx ? value : p)));

  return (
    <>
      {phones.map((phone, i) => (
        <div key={i}>
          <input value={phone}
                 onChange={(e)=> updateField(e.target.value, i)} />
          <button onClick={() => removeField(i)}>Remove</button>
        </div>
      ))}

      <button onClick={addField}>Add Phone Number</button>
    </>
  );
}
```

---

### ✔ Explanation

* Array of inputs stored in state
* Add → push item
* Remove → filter
* Update → map
* Perfect for forms like "add multiple contacts"

---

# ======================================================

# ✅ **14. Upload Resume With File Size Limit (2MB Max)**

======================================================

---

## ⭐ File Upload Validation

```jsx
function ResumeUpload() {
  const [error, setError] = useState("");

  const handleFile = (e) => {
    const file = e.target.files[0];
    if (file.size > 2 * 1024 * 1024) {
      setError("File size must be less than 2MB");
      return;
    }
    setError("");
    alert("File accepted: " + file.name);
  };

  return (
    <>
      <input type="file" accept=".pdf,.doc,.docx" onChange={handleFile} />
      {error && <p style={{ color: "red" }}>{error}</p>}
    </>
  );
}
```

---

### ✔ Explanation

* Reads file size from File API (`file.size`)
* Compares with 2MB
* Rejects file and displays error
* Accepts resume formats `.pdf`, `.docx`

---

# ======================================================

# ✅ **15. Validate PAN/Aadhar or Other Indian IDs**

======================================================

---

## ⭐ PAN Validation

Format: `ABCDE1234F` → **5 letters + 4 digits + 1 letter**

```js
function validatePAN(pan) {
  return /^[A-Z]{5}[0-9]{4}[A-Z]{1}$/.test(pan);
}
```

---

## ⭐ Aadhaar Validation

12 digits only, cannot start with 0 or 1.

```js
function validateAadhaar(aadhaar) {
  return /^[2-9]{1}[0-9]{11}$/.test(aadhaar);
}
```

---

## ⭐ Usage Example

```jsx
function IDValidation() {
  const [id, setId] = useState("");
  const [error, setError] = useState("");

  const handleValidate = () => {
    if (validatePAN(id) || validateAadhaar(id)) {
      setError("");
      alert("Valid ID");
    } else {
      setError("Invalid PAN or Aadhaar");
    }
  };

  return (
    <>
      <input placeholder="Enter PAN/Aadhaar"
             onChange={(e)=> setId(e.target.value.toUpperCase())}/>
      <button onClick={handleValidate}>Validate</button>
      {error && <p style={{ color:"red" }}>{error}</p>}
    </>
  );
}
```

---

### ✔ Explanation

* PAN must match alphanumeric rules
* Aadhaar must be 12-digit and not start with 0/1
* Converts PAN input to uppercase automatically

---

# 🎯 FINAL INTERVIEW SUMMARY

| Feature                   | Concept                         |
| ------------------------- | ------------------------------- |
| Complex signup validation | Regex + matching fields         |
| Multi-step form           | Step-based conditional UI       |
| Dynamic fields            | Array-based form inputs         |
| Resume upload limit       | File API + size validation      |
| PAN/Aadhaar validation    | Regex based on Indian ID format |

These tasks demonstrate **real-world problem solving** expected from modern React developers.

---


Just say **“Next React tasks”**.
