### 👋 Hi, I'm Sajitha Mathi
🚀 Software Engineer | Full-Stack, with a focus on AI/ML-backed products

<p align="center">
  <img src="https://komarev.com/ghpvc/?username=sajithamathi19&color=blueviolet&style=flat" alt="Profile views" />
</p>

<sub>This is a new account — my previous one was accidentally deleted. Older commit history and contributions are still attributed to me via my original commit email.</sub>

I build complete, production-shaped systems end to end — backend APIs, databases, scheduling infrastructure, and frontends — with AI/ML woven in where it actually earns its place: agentic pipelines, structured LLM generation, and closed feedback loops, not bolted-on prompts.

---

### 🧠 What I Do
- Build full-stack applications across the stack: FastAPI/Node.js/Spring Boot backends, React/Streamlit frontends, PostgreSQL/SQLite/Firebase persistence
- Build multi-agent LLM pipelines that discover, generate, review, and self-correct — hand-orchestrated directly on LLM APIs (Claude, Gemini, Groq) rather than black-box frameworks
- Design closed-loop systems that verify real-world outcomes and feed them back into future decisions (reflection/learning loops, not just static prompts)
- Build reliability layers around LLM output: structured/validated generation instead of free-text parsing, multi-stage automated review, reputation/trust scoring

---

### 🌱 Open Source

**[Microsoft PyRIT](https://github.com/microsoft/PyRIT)** (Python Risk Identification Tool for generative AI):
- **[#1831](https://github.com/microsoft/PyRIT/pull/1831)** — merged — added the SALT-NLP Moral Integrity Corpus (MIC) dataset loader
  <sub>*Originally authored and merged from my previous GitHub account, which was accidentally deleted — the PR page shows "ghost" as a result, but the underlying commits are still attributed to me (verified via my original commit email).*</sub>
- **[#1910](https://github.com/microsoft/PyRIT/pull/1910)** — merged — fixed a temp-file leak and race condition in `save_formatted_audio`
  <details>
  <summary>Details</summary>

  **Problem**

  `DataTypeSerializer.save_formatted_audio` had two bugs in the Azure storage branch:
  - **File leak**: `os.remove(local_temp_path)` was not in a `finally` block, so if the Azure upload raised an exception, the temp `.wav` file was never deleted.
  - **Race condition**: the temp file always used the fixed name `temp_audio.wav`, so concurrent calls would clobber each other's WAV before upload.

  **Fix**
  - Replaced the fixed `temp_audio.wav` name with `tempfile.NamedTemporaryFile` to give each call a unique path.
  - Wrapped the upload block in `try`/`finally` so the temp file is always deleted.

  **Tests**
  - Added a regression test that mocks the Azure upload to raise, then asserts no new `.wav` files remain in `DB_DATA_PATH`.

  Fixes #1894.

  *Note: this PR was originally authored and merged from my previous GitHub account, which was accidentally deleted. The PR page shows "ghost" as a result, but the underlying commits are still attributed to me (verified via my original commit email).*
  </details>
- **[#2301](https://github.com/microsoft/PyRIT/pull/2301)** — in review — implements the Bijection Attack (arXiv:2410.01294) as a new converter/attack module
