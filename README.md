# ClipCite

**Fair Use Citation Infrastructure for Video Culture** 

---

## The Problem

Video has become how people experience, discuss, and quote culture. Yet current copyright enforcement treats all video quotation as piracy, systematically suppressing fair use rights through automated systems operated by platforms with financial incentive to side with copyright holders. 

**Fair use is legal.** Section 107 of the Copyright Act explicitly permits quotation for criticism, comment, news reporting, teaching, scholarship, and research. The copyright holder has the right to assert copyright infringement, to request removal of the alledged infringing content, and to escalate to the courts for infringement rulings. None of these actions includes allowing a platform to use an algorithm to target remove free speech and prevent fair use from public access.

**Fair use is suppressed.** YouTube's Content ID flags video automatically. It cannot distinguish between a full movie and a 30-second clip used for commentary. Copyright holders issue takedowns without evidence of infringement. Users can counter-claim, but the technology only allows a limited appeal process, which favors the copyright holders alledging infringement, rather than protect the public's free speech from copyright holders accusations of infringement. This allows the copyright claimant to judge fair use which is not their right by law.  

**The result:** A student quoting a film scene for an essay, a mom sharing a clip that moved her, a critic analyzing a movie—all face suppression not because they're infringing, but because platforms created automated systems that can't tell the difference between piracy and quotation. *Hint: Disliking fair use, doesn't mean every use is copyright abuse.*

---

## The Solution

ClipCite provides **public infrastructure for fair use citation.**

We assume your intent is educational. We document that intent. We refuse to automate takedowns. We make copyright claims transparent. We give you the right to respond. 

### How It Works

**1. Upload or Link a Clip**
- Provide your video (as a file or link to existing video)

**2. Add Context**
- Title, timestamp, description, purpose, keywords
- This metadata documents your educational intent

**3. Auto-Generate Citation**
- Proper attribution in APA, MLA, Chicago formats
- Your claim to fair use, properly formatted

**4. Publish**
- Your clip is public with full metadata visible
- Other people can search, view, and learn from it

**5. If Challenged**
- Copyright holder issues DMCA notice
- We log it. We notify you. You get 10 business days to respond with fair use arguments.
- Your clip doesn't disappear while you prepare your defense.

**6. Documentation**
- All records kept for legal clarity
- If challenged in court, you have documented good faith

**7. You Control Visibility**
- Keep your clip public (DMCA claims visible in metadata) or privatize it
- All challenges & your rebuttals become part of the permanent, public record
- Copyright holders know frivolous claims will be visible

---

## Core Principle: Free Speech Before Corporate Takedown

ClipCite prioritizes your right to quote over corporate pressure to suppress quotation.

We do this by:
- **Documenting good faith intent** (metadata at submission)
- **Rejecting automation** (human judgment required)
- **Making claims transparent** (no hidden suppression)
- **Giving users voice** (10 days + public platform to respond)
- **Creating legal paper trail** (audit log for court defense)

**Why this works:** When copyright holders know their claims will be visible and users can respond publicly, frivolous takedowns drop dramatically. They can no longer silently suppress speech. Transparency is the best defense against abuse of power.

---

## Legal Framework

### Fair Use Is Real

Fair use is not a request for permission—it is a legal defense determined by courts. The four fair use factors are:

1. **Purpose and Character** - Is your use transformative? (commentary, criticism, scholarship, education vs. commercial reproduction)
2. **Nature of the Work** - What kind of work is it? (transformative uses of creative works get stronger protection)
3. **Amount Used** - How much did you use? (using only what's necessary strengthens fair use)
4. **Market Impact** - Does your use harm the market for the original? (quotation usually doesn't; posting the full movie does)

### ClipCite Strengthens Fair Use Defense

- **Documented educational purpose** supports transformative use argument
- **Transparent metadata** shows intent and necessity
- **User-facing DMCA logging** demonstrates good faith compliance
- **Permanent records** create legal paper trail for court defense

### DMCA Safe Harbor Compliance

ClipCite complies with DMCA safe harbor: we log notices, notify users, require user response, and document all actions. We don't ignore copyright claims. We require humans to evaluate them before any action. This demonstrates good faith and distinguishes us from systems that profit from suppression.

---

## Getting Started

### Run the Prototype

The working prototype is a fully functional web application built with HTML/CSS/JavaScript.

**To view locally:**
1. Download `prototype/index.html`
2. Open in any web browser
3. Try uploading a clip, viewing metadata, opening modals

**Features:**
- ✅ Clip upload/link interface
- ✅ Metadata form (title, timestamp, purpose, keywords)
- ✅ Auto-generated citations (APA, MLA, Chicago)
- ✅ Tab navigation (About, Upload, My Clips)
- ✅ Modal windows (DMCA Guide, Legal Framework)
- ✅ Clip management and storage (browser localStorage)
- ✅ Professional UI with dark theme

**Note:** This is a client-side prototype. For production, you'll need to add a backend (Firebase, Node.js, etc.) to handle file storage and DMCA management.

---

## Documentation

### Papers & Analysis

All papers are in `/Papers/`:

- **[White Paper](Papers/)** - Comprehensive argument for fair use citation infrastructure. The problem, the solution, legal framework, and implementation vision.

- **[Blue Paper](Papers/)** - Technical architecture and implementation details. Data model, API design, technology stack, DMCA workflow, cost estimation.

- **[Academic Paper](Papers/)** - Scholarly analysis for legal professionals and academics. Fair use doctrine, platform power, copyright enforcement, and how design can restore fair use.

- **[One-Pager](Papers/)** - Executive summary for quick reference. Perfect for investors and partners.

### Project Documentation

- **[Philosophy Document](Philosophy.md)** - Complete philosophy statement. The 7-point operating model, why transparency defeats frivolous takedowns, and what this means for culture.

- **[Implementation Guide](Implementation.md)** - Full technical roadmap. Architecture options, feature breakdown, DMCA workflow, backend design, deployment strategy.

- **[Data Schema](schema/clip_citation_schema.json)** - Complete data model for clips, DMCA notices, users, and citations.

---

## Architecture

### Data Model

**Clips**
- clipId, uploaderId, uploadDate
- source (UPLOAD or LINK)
- metadata (auto-detected and user-submitted)
- compliance status and DMCA history
- auto-generated citations

**DMCA Notices**
- noticeId, clipId, dateReceived
- claimant and claim reason
- status (PENDING, DISPUTED, UPHELD, WITHDRAWN)
- user response with fair use argument
- platform action and notes

**Users**
- email, username, profile
- clipsSubmitted, dmcaClaimsReceived, dmcaDisputesWon

**Audit Log**
- Every action logged: timestamp, actor, target, details
- Permanent record for legal clarity

### Technology Stack

**Frontend**
- HTML/CSS/JavaScript (current prototype)
- React.js recommended for production

**Backend Options**

*Option A: Firebase (Recommended for MVP)*
- Firestore (database)
- Cloud Functions (serverless backend)
- Cloud Storage (video files)
- Firebase Auth

*Option B: Self-Hosted*
- Node.js + Express or Python + FastAPI
- PostgreSQL database
- S3-compatible storage (MinIO)
- Docker deployment

**Cost Estimate (50K users, 10K monthly submissions):**
- Firebase: $400-900/month
- Self-hosted: $165-315/month

---

## API Design

### Clips
- `POST /clips` - Create new clip
- `GET /clips/:clipId` - Retrieve clip
- `PUT /clips/:clipId` - Update metadata
- `DELETE /clips/:clipId` - Delete clip
- `GET /clips?search=query` - Search clips
- `GET /user/clips` - Get user's clips

### DMCA
- `POST /dmca/notices` - Submit notice
- `GET /dmca/notices/:noticeId` - Retrieve notice
- `POST /dmca/notices/:noticeId/response` - Submit counter-notification
- `GET /clips/:clipId/dmca` - Get all notices on clip

### Authentication
- `POST /auth/signup` - Create account
- `POST /auth/login` - User login
- `GET /auth/user` - Current user

---

## Development Roadmap

### Phase 1: MVP (Weeks 1-4)
- User authentication
- Clip upload/link
- Metadata form
- Citation generation
- User dashboard

### Phase 2: Core (Weeks 5-8)
- DMCA notice intake
- Email notifications
- User response mechanism
- Clip visibility toggle
- Audit log

### Phase 3: Polish (Weeks 9-12)
- Fair use education content
- DMCA notice templates
- Data export
- Public search/browse
- Analytics

### Phase 4: Scale
- Video transcoding
- Improved search
- Community features
- Rights-holder engagement
- Legal partnerships

---

## Legal Position

**This is not neutral infrastructure.**

We believe:
- Fair use rights are real and must be protected
- Video quotation is legitimate discourse
- People should discuss and analyze culture without facing automated suppression
- Burden of proof belongs on copyright holders, not users
- Platforms can support fair use through thoughtful design

**Our commitment:**
- We will not auto-suppress fair use
- We will document educational intent
- We will refuse automation in legal determinations
- We will make copyright claims transparent
- We will support user response opportunity

If copyright holders try to pressure us to auto-suppress, we'll resist. If they sue, our position is clear: we're infrastructure for citation compliance, and we support fair use rights.

---

## Contributing

ClipCite is open to contributions. We're looking for:

- **Developers** - Help build the backend, improve the frontend, add features
- **Legal experts** - Review documentation, help prepare for litigation, advise on compliance
- **Designers** - Improve UI/UX, create educational materials
- **Academics** - Write analyses, help publish research
- **Community members** - Use it, give feedback, share your story

See [CONTRIBUTING.md](CONTRIBUTING.md) for details.

---

## License

- **Documentation & Papers**: [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) - Use, remix, and share freely
- **Code**: [AGPL 3.0](https://www.gnu.org/licenses/agpl-3.0.html) - Open source with copyleft provision
- **Philosophy**: Public domain - This vision is for everyone

---

## Status

✅ **Working Prototype** - Full web interface with clip upload, metadata, citations, modal windows

✅ **Philosophy & Documentation** - 7 comprehensive documents explaining the vision, legal position, and implementation

✅ **Data Schema** - Complete model for clips, DMCA notices, users, citations

⏳ **Next Steps** - Legal review, backend implementation, beta testing with real users

---

## Contact

- **Website**: (coming soon)
- **Email**: (coming soon)
- **GitHub Issues**: Report bugs, suggest features, ask questions
- **Discussions**: Community conversation about fair use, platform power, and digital culture

---

## The Bigger Picture

Video is how culture is quoted now. A mom sharing a clip that moved her, a student analyzing a film, a critic discussing cinema—these are acts of quotation, not piracy. They deserve protection, not suppression.

ClipCite proves that platforms can support fair use. By documenting intent, refusing automation, and making claims transparent, we return judicial power to where it belongs: courts, not algorithms.

**The future of culture depends on the ability to quote it. ClipCite enables that future.**

---

Made with ❤️ for fair use, free speech, and the right to quote culture.

**Free Speech Before Corporate Takedown.**
