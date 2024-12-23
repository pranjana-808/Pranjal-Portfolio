   <script>
    const commentForm = document.getElementById('commentForm');
    const commentsList = document.getElementById('commentsList');

    commentForm.addEventListener('submit', function(event) {
      event.preventDefault();

      // Get user input
      const username = document.getElementById('username').value;
      const rating = document.getElementById('rating').value;
      const comment = document.getElementById('comment').value;

      // Validate rating
      if (rating < 1 || rating > 10) {
        alert("Please enter a rating between 1 and 10.");
        return;
      }

      // Create new comment element
      const commentItem = document.createElement('div');
      commentItem.classList.add('comment-item');
      commentItem.innerHTML = `
        <p><strong>${username}</strong> (Rating: ${rating}/10)</p>
        <p>${comment}</p>
      `;

      // Add comment to the list
      commentsList.appendChild(commentItem);

      // Clear form
      commentForm.reset();
    });

    function updateComments() {
      commentsList.innerHTML = ''; // Clear existing comments

      const commentsToShow = comments.slice(0, 3); // Get top 3 comments
      commentsToShow.forEach(comment => {
        const commentItem = document.createElement('div');
        commentItem.classList.add('comment-item');
        commentItem.innerHTML = `
          <p><strong>${comment.username}</strong> (Rating: ${comment.rating}/10)</p>
          <p>${comment.comment}</p>
        `;
        commentsList.appendChild(commentItem);
      });

      // Show or hide "Show More" button
      if (comments.length > 3) {
        showMoreBtn.style.display = 'block';
      } else {
        showMoreBtn.style.display = 'none';
      }
    }

    // Handle "Show More" button click
    showMoreBtn.addEventListener('click', function() {
      commentsList.innerHTML = ''; // Clear existing comments
      comments.forEach(comment => {
        const commentItem = document.createElement('div');
        commentItem.classList.add('comment-item');
        commentItem.innerHTML = `
          <p><strong>${comment.username}</strong> (Rating: ${comment.rating}/10)</p>
          <p>${comment.comment}</p>
        `;
        commentsList.appendChild(commentItem);
      });
      showMoreBtn.style.display = 'none'; // Hide "Show More" button
    });



  </script>