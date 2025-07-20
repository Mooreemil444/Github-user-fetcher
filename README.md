<script>
  function fetchMultipleUsers(count = 5) {
    fetch(`https://randomuser.me/api/?results=${count}`)
      .then(response => {
        if (!response.ok) throw new Error('Failed to fetch');
        return response.json();
      })
      .then(data => {
        const users = data.results.map(user => ({
          name: `${user.name.first} ${user.name.last}`,
          email: user.email,
          picture: user.picture.large
        }));

        // Save to localStorage
        localStorage.setItem('randomUsers', JSON.stringify(users));

        console.log(`✅ ${count} users saved to localStorage`);
        console.table(users);
      })
      .catch(error => {
        console.error('❌ Error:', error.message);
      });
  }

  fetchMultipleUsers(10); // Fetch and store 10 users
</script>
