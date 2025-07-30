## Future Updates / Ideas

This section outlines potential features and improvements for future versions of Multiplerblx.

### 🚀 Planned Features & Enhancements

*   **Built-in Chat Logger:**
    *   Implement a feature to capture and log in-game chat messages for selected accounts.
    *   This would require deeper integration or injection techniques, which are significantly more complex than the current token-based automation.

*   **Multi-Game Support:**
    *   Investigate the feasibility of extending core automation features (account switching, launching) to other platforms like CSGO or Fortnite.
    *   Note: This would likely require significant architectural changes and platform-specific implementations, moving beyond Roblox's token system.

*   **AI-Powered Chat Analysis (Opt-in):**
    *   *Concept:* Offer an optional feature where users can contribute collected chat logs to RoCheck for AI training/analysis.
    *   *Implementation:*
        *   Add a clear prompt (e.g., every 20-30 minutes) asking the user if they wish to upload collected chat logs.
        *   Include explicit consent language: "By selecting 'Yes', you agree to allow RoCheckRblx/RoCheck to collect the chat logs gathered by this tool for AI analysis."
        *   Ensure a clear 'No' option is always available, and respect the user's choice persistently.
        *   Implement secure, anonymized data upload mechanisms if consent is given.
          

### 🧪 Experimental / Advanced Ideas

*   **Enhanced Presence Detection:**
    *   Monitor account activity beyond just game presence (e.g., website activity if possible via cookies).
*   **Automated Task Scheduler UI:**
    *   Provide a graphical interface to schedule more complex tasks (e.g., join Game A at 9 AM, switch to Game B at 11 AM, send message X at 1 PM) rather than just the daily 8 AM join.
*   **Improved Resource Management:**
    *   Dynamically adjust batch sizes and concurrency limits for launching/monitoring based on system resource usage (CPU, RAM) to prevent system slowdowns.
*   **Plugin/Scripting System:**
    *   Allow users to write simple scripts (e.g., in Lua or a custom DSL) to define custom bot behaviors or automation sequences.
*   **Account Grouping/Profiles:**
    *   Let users create groups or profiles for accounts (e.g., "Group A for Game X", "Friends Accounts") and perform actions on entire groups.

### 🛡️ Potential Improvements

*   **Security Hardening:**
    *   Review and enhance token encryption/storage methods.
    *   Implement process sandboxing or isolation for launched Roblox instances if possible.
*   **Performance Optimization:**
    *   Further optimize API calls and UI updates for handling very large numbers of accounts.
    *   Investigate memory leaks or performance bottlenecks over extended use.
*   **UI/UX Refinements:**
    *   Improve the layout and information density of account cards.
    *   Add sorting and filtering options for the account list (`lstAccounts`).
    *   Implement a more robust settings system (e.g., saving/loading settings to/from a file).
