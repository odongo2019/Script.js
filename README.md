// Toggle mobile navigation menu
function toggleMenu() {
  const nav = document.querySelector("nav ul");
  nav.classList.toggle("active");
}

// Smooth scrolling
document.querySelectorAll('nav a').forEach(link => {
  link.addEventListener('click', event => {
    event.preventDefault();
    const targetId = link.getAttribute('href');
    document.querySelector(targetId).scrollIntoView({
      behavior: 'smooth'
    });
  });
});

// Filter projects
function filterProjects(category) {
  const projects = document.querySelectorAll('#projects article');

  projects.forEach(project => {
    if (category === 'all' || project.dataset.category === category) {
      project.style.display = 'block';
    } else {
      project.style.display = 'none';
    }
  });
}

// Lightbox for project images
const images = document.querySelectorAll('#projects img');
const modal = document.createElement('div');
modal.id = 'lightbox';
document.body.appendChild(modal);

images.forEach(image => {
  image.addEventListener('click', () => {
    modal.classList.add('active');
    const img = document.createElement('img');
    img.src = image.src;

    while (modal.firstChild) {
      modal.removeChild(modal.firstChild);
    }

    modal.appendChild(img);
  });
});

modal.addEventListener('click', () => {
  modal.classList.remove('active');
});

// Contact form validation
const form = document.querySelector('form');

form.addEventListener('submit', event => {
  event.preventDefault();

  const name = document.querySelector('#name');
  const email = document.querySelector('#email');
  const message = document.querySelector('#message');

  if (!name.value || !email.value || !message.value) {
    alert('Please fill in all required fields.');
    return;
  }

  alert('Message sent successfully!');
  form.reset();
});
