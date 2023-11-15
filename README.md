# CSS-Learn
Files from Udemy Web Dev Course
- 
 <ul>
        {[...(new Set(userDetails.authorities
          .map(authority => authority.role.toLowerCase())
          .filter(role => role.includes('operate') || role.includes('admin') || role.includes('support'))
        ))].map((role, index) => (
          <li key={index}>{role}</li>
        ))}
      </ul>
