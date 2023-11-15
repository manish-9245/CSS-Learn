# CSS-Learn
Files from Udemy Web Dev Course
const InactivityPopup = () => {
  const [inactiveTime, setInactiveTime] = useState(0);
  const popupTimeout = 2 * 60 * 1000; // 2 minutes in milliseconds

  useEffect(() => {
    const resetTimer = () => {
      clearTimeout(inactiveTime);
      setInactiveTime(setTimeout(showPopup, popupTimeout));
    };

    const showPopup = () => {
      // Display your popup here
      alert('Hey there! You have been inactive for more than 2 minutes.');
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
      clearTimeout(inactiveTime);
      window.removeEventListener('mousemove', handleUserActivity);
      window.removeEventListener('keypress', handleUserActivity);
    };
  }, [inactiveTime]);
