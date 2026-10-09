# Closing a session

Do these in order at the end of every working session, so the next session starts where this one stopped. Follow the project's own instructions where they differ, and where they say something must not be saved outside the project folder, keep it inside.

1. **Save the user's prompts, if the project keeps a prompt library.** Find the prompts the user wrote themselves in this session, not a starter prompt they pasted, and not a message that is only the request to save them. Put them in the project's prompt file, one per numbered slot, exactly as typed. Keep typos, lowercase and missing punctuation. If the file has fewer slots than prompts, add more. If the project uses a different convention, follow that.
2. **Update the working context** with what was figured out and is not recorded yet. Add a dated section instead of rewriting history. For each item say whether it is verified (from a source) or inferred, and list what is still open. Keep it short enough to be read at the start of the next session.
3. **Check what changed** before committing: list the changed and new files, and confirm nothing private or unrelated is included.
4. **Commit and push only when the user asks.** Use a short message that says what the session did. Add any attribution line the project requires. Push to the branch the user names.
5. **Report back** in a few lines: what was saved and where, the commit reference, and the link to the repository. If a step could not run, say so plainly.

If a tool fails on a step (a transient permission error, for example), say so, keep the files saved, and retry when asked.
