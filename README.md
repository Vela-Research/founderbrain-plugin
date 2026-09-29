# FounderBrain for Claude

FounderBrain analyses how one person talked in a meeting and compares it with 773 public interviews of founders and operators. You give Claude a transcript of a pitch, an investor call, a sales call or an interview. FounderBrain returns your speaking type, where you sit on four speaking styles, the well-known founder you sound most like, the habits that stand out, two things to try next time and one to keep. Claude then coaches you on it, using moments from the meeting.

The analysis describes one conversation, not your personality. Neither end of a style is better.

## What is in this plugin

- **The FounderBrain connector.** A remote MCP server at `https://mcp.thinkreasonlearn.com/mcp`. It has no sign in.
- **The `coach-meeting` skill.** It tells Claude how to run an analysis of a transcript you attach or paste, and how to coach from the result.
- **The `prepare-transcript` skill.** It tells Claude how to turn exports from Zoom, Meet, Teams, Otter, Fireflies or caption files into one speaker turn per line, without changing any words.

## Tools

| Tool | What it does |
|---|---|
| `check_transcript` | Lists the speakers in a transcript and how many words each said. Nothing is scored. |
| `analyse_transcript` | Analyses one speaker and returns the report as data. In Claude on the web and desktop the full report also appears in the chat. The analysis usually takes under a minute, after Claude has sent the transcript, which can take a few minutes for a long meeting. |

Both only read. None of them changes anything anywhere.

## Try it

- "Here's the transcript of my seed pitch yesterday. How did I come across?"
- "I'm Speaker 1 in this call with an investor. What should I work on before my next pitch?"
- "I have a Series A meeting tomorrow. Based on this last pitch, what should I keep doing?"

## Other apps

- **Codex.** Run `codex mcp add founderbrain --url https://mcp.thinkreasonlearn.com/mcp`. You get the results and coaching as text.
- **Skills only.** Run `npx skills add Vela-Research/founderbrain-plugin` to add the two skills to an agent that supports them, then add the connector address above.

## Limits

- One transcript of up to 15,000 words.
- The person you choose needs at least 300 words of their own. Around 3,000 words gives a settled result.
- Each line should be one speaker turn, such as `Ana: We started in 2024 ...`. The `prepare-transcript` skill handles most exports.
- The service has hourly limits, a few analyses an hour for each person and a shared limit for everyone. If it is busy, try again later.

## Where your data goes

- The transcript goes from Claude to the FounderBrain server at `https://mcp.thinkreasonlearn.com/mcp` and nowhere else.
- It is scored on that server by our own model and deleted when the analysis finishes. We do not store transcripts, names or reports, and we do not train on them.
- The report in the chat loads its script and fonts from the same server.
- Our logs hold word counts, timings and error types, never text or names.
- Your Claude conversation, including the transcript, is kept by Anthropic under its own terms.

The full privacy policy is at https://thinkreasonlearn.com/privacy.

## Troubleshooting

- **"No speaker turns were found."** The transcript is not one speaker per line. Ask Claude to prepare the transcript first.
- **"Only N words of answers were found."** The person you picked spoke too little. Try a longer meeting.
- **"Busy" or "as many transcripts as it will in an hour."** The service is at capacity. Try again in a few minutes.
- **The report does not appear in the chat.** Some apps, such as Claude Code, cannot show it. Claude still gets the full result and coaches from it.

## Support

Email support@thinkreasonlearn.com. See SUPPORT.md and https://thinkreasonlearn.com/founderbrain.

## Licence

See LICENSE.
