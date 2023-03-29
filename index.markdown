---
layout: base
---

<h1>Supercharged hospitality</h1>
<p>Shine is a modern, people–focused platform for managing your guests.</p>
 
<div class="cta">
  <p>Be one of the first to try Shine and learn how we're making life better for property owners.</p>
  <form id="initial-form" action="https://formspree.io/f/xpzejvoa" method="POST" >
    <input type="email" name="email" placeholder="Enter email" />
    <button type="submit">
      Get updates 
      <svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path fill-rule="evenodd" clip-rule="evenodd" d="M21.4631 12.753L1.50018 12.753L1.50018 11.2472L21.4632 11.2472L21.4631 12.753Z" fill="white"/>
        <path fill-rule="evenodd" clip-rule="evenodd" d="M12.5253 1.50012L22.5 12.0001L12.5253 22.5001L11.4883 21.4085L20.4259 12.0001L11.4883 2.59176L12.5253 1.50012Z" fill="white"/>
      </svg>
    </button>
    <div id="form-status"></div>
  </form>
</div>

<script>
  var form = document.getElementById("initial-form");
  
  async function handleSubmit(event) {
    event.preventDefault();
    var status = document.getElementById("form-status");
    var data = new FormData(event.target);
    fetch(event.target.action, {
      method: form.method,
      body: data,
      headers: {
          'Accept': 'application/json'
      }
    }).then(response => {
      if (response.ok) {
        status.innerHTML = "Thanks for your submission!";
        form.reset()
      } else {
        response.json().then(data => {
          if (Object.hasOwn(data, 'errors')) {
            status.innerHTML = data["errors"].map(error => error["message"]).join(", ")
          } else {
            status.innerHTML = "Oops! There was a problem submitting your form"
          }
        })
      }
    }).catch(error => {
      status.innerHTML = "Oops! There was a problem submitting your form"
    });
  }
  form.addEventListener("submit", handleSubmit)
</script>