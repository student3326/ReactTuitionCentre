import React, { useState } from "react";

// Simple React project for Tuition Centre
// Using subject-related photo links instead of human photos

export default function TuitionCenterApp() {
  const [contact, setContact] = useState({ name: "", email: "", message: "" });
  const [submitted, setSubmitted] = useState(false);

  const teachers = [
    {
      name: "Ramesh Kumar",
      subject: "Mathematics",
      qualification: "M.Sc. Mathematics (IIT Delhi); B.Ed.",
      image: "https://images.pexels.com/photos/590493/pexels-photo-590493.jpeg", // math formulas board
    },
    {
      name: "Sita Sharma",
      subject: "English",
      qualification: "M.A. English Literature (JNU); NET Qualified",
      image: "https://images.pexels.com/photos/261909/pexels-photo-261909.jpeg", // open book
    },
    {
      name: "Anil Verma",
      subject: "Physics",
      qualification: "M.Sc. Physics (IISc Bangalore)",
      image: "https://images.pexels.com/photos/256417/pexels-photo-256417.jpeg", // atom model
    },
    {
      name: "Priya Nair",
      subject: "Chemistry",
      qualification: "M.Sc. Chemistry (University of Delhi)",
      image: "https://images.pexels.com/photos/2280547/pexels-photo-2280547.jpeg", // chemistry lab
    },
    {
      name: "Arjun Patel",
      subject: "Computer Science",
      qualification: "B.Tech Computer Science; M.Tech (IIT Bombay)",
      image: "https://images.pexels.com/photos/1181673/pexels-photo-1181673.jpeg", // laptop code
    },
  ];

  function handleChange(e) {
    setContact({ ...contact, [e.target.name]: e.target.value });
  }

  function handleSubmit(e) {
    e.preventDefault();
    setSubmitted(true);
    setTimeout(() => setSubmitted(false), 3000);
    setContact({ name: "", email: "", message: "" });
  }

  return (
    <div style={{ fontFamily: "Arial, sans-serif", lineHeight: 1.6, background: "#f9f9f9", color: "#333" }}>
      {/* Header */}
      <header style={{ background: "#4a4aee", color: "white", padding: "15px 0", textAlign: "center" }}>
        <h1>BrightPath Tuition Centre</h1>
        <p>Guiding Students to Success</p>
      </header>

      {/* Banner */}
      <section style={{ textAlign: "center", padding: "30px 20px", background: "#eef2ff" }}>
        <img
          src="https://images.pexels.com/photos/4144222/pexels-photo-4144222.jpeg"
          alt="Classroom banner"
          style={{ width: "100%", maxWidth: "700px", borderRadius: "10px" }}
        />
        <h2 style={{ marginTop: "20px", color: "#333" }}>Achieve Your Academic Goals with Expert Teachers</h2>
        <p>Join our interactive and result-oriented classes today!</p>
      </section>

      {/* About */}
      <section id="about" style={{ padding: "20px", maxWidth: "800px", margin: "auto" }}>
        <h2>About Us</h2>
        <p>
          BrightPath Tuition Centre focuses on delivering quality education for school and college students. We have experienced
          subject teachers who make learning simple and effective through practical explanations and tests.
        </p>
      </section>

      {/* Teachers */}
      <section id="teachers" style={{ background: "white", padding: "30px 20px" }}>
        <h2 style={{ textAlign: "center", marginBottom: "20px" }}>Our Teachers</h2>
        <div style={{ display: "flex", flexWrap: "wrap", justifyContent: "center", gap: "20px" }}>
          {teachers.map((t) => (
            <div
              key={t.name}
              style={{
                width: "220px",
                background: "#fafafa",
                border: "1px solid #ddd",
                borderRadius: "10px",
                textAlign: "center",
                padding: "10px",
              }}
            >
              <img
                src={t.image}
                alt={t.name}
                style={{ width: "100%", height: "160px", objectFit: "cover", borderRadius: "10px" }}
              />
              <h3 style={{ marginTop: "10px" }}>{t.name}</h3>
              <p style={{ fontWeight: "bold", color: "#555" }}>{t.subject}</p>
              <p style={{ fontSize: "14px", color: "#666" }}>{t.qualification}</p>
            </div>
          ))}
        </div>
      </section>

      {/* Contact */}
      <section id="contact" style={{ padding: "30px 20px", background: "#eef2ff" }}>
        <h2 style={{ textAlign: "center" }}>Contact Us</h2>
        <form
          onSubmit={handleSubmit}
          style={{ display: "flex", flexDirection: "column", gap: "10px", maxWidth: "400px", margin: "20px auto" }}
        >
          <input
            type="text"
            name="name"
            value={contact.name}
            onChange={handleChange}
            placeholder="Your Name"
            required
            style={{ padding: "10px", borderRadius: "5px", border: "1px solid #ccc" }}
          />
          <input
            type="email"
            name="email"
            value={contact.email}
            onChange={handleChange}
            placeholder="Your Email"
            required
            style={{ padding: "10px", borderRadius: "5px", border: "1px solid #ccc" }}
          />
          <textarea
            name="message"
            value={contact.message}
            onChange={handleChange}
            placeholder="Your Message"
            style={{ padding: "10px", borderRadius: "5px", border: "1px solid #ccc", minHeight: "80px" }}
          ></textarea>
          <button type="submit" style={{ background: "#4a4aee", color: "white", padding: "10px", border: "none", borderRadius: "5px" }}>
            Send Message
          </button>
          {submitted && <p style={{ color: "green", textAlign: "center" }}>Message Sent Successfully!</p>}
        </form>
      </section>

      {/* Footer */}
      <footer style={{ background: "#333", color: "white", textAlign: "center", padding: "15px" }}>
        <p>© {new Date().getFullYear()} BrightPath Tuition Centre | All Rights Reserved</p>
      </footer>
    </div>
  );
}
