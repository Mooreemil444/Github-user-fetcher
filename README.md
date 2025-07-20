<script>
  function fetchRandomUser() {
    fetch('https://randomuser.me/api/')
      .then(response => {
        if (!response.ok) throw new Error('Failed to fetch');
        return response.json();
      })
      .then(data => {
        const user = data.results[0];
        const userData = {
          name: `${user.name.first} ${user.name.last}`,
          email: user.email,
          picture: user.picture.large
        };

        // Save to localStorage
        localStorage.setItem('randomUser', JSON.stringify(userData));

        console.log('✅ User saved to localStorage:', userData);
      })
      .catch(error => {
        console.error('❌ Error:', error.message);
      });
  }

  fetchRandomUser();
</script>
