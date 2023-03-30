---
layout: base
---

<section class="section-content">

  <div class="block-hero">
    <h1>Supercharged hospitality</h1>
    <p>Shine is a modern, people–focused platform for managing your guests.</p>
  </div>
   
  <div class="block-cta">
    <p>Be one of the first to try Shine and learn how we're making life better for property owners.</p>
    {%- include subscribe.html formId="xpzejvoa" -%}
  </div>

</section>

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