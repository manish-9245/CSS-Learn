# CSS-Learn
Files from Udemy Web Dev Course
- 
  const [inactiveTime, setInactiveTime] = useState(0);
  const popupTimeout = 2 * 60 * 1000; // 2 minutes in milliseconds

  useEffect(() => {
    let timeoutId;

    const resetTimer = () => {
      clearTimeout(timeoutId);
      timeoutId = setTimeout(() => {
        // Display your popup here
        alert('Hey there! You have been inactive for more than 2 minutes.');
      }, popupTimeout);
    };

    const handleUserActivity = () => {
      resetTimer();
    };

    // Event listeners for user activity
    window.addEventListener('mousemove', handleUserActivity);
    window.addEventListener('keypress', handleUserActivity);

    // Start the initial timer
    resetTimer();

    // Cleanup function to remove event listeners and clear timeout on unmounting
    return () => {
      clearTimeout(timeoutId);
      window.removeEventListener('mousemove', handleUserActivity);
      window.removeEventListener('keypress', handleUserActivity);
    };
  }, []);
