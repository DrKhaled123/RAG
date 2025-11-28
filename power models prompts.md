power models prompts.md

New Chat

Share

Yupp Logo
Toggle Sidebar
Refer for rewards
Khaled Alzayat
Dark mode

Khaled Alzayat

convert the following to ready copy paste prompt used generlly for any web app , for web making exams for students frpm pdf / backend frontend and convert json to dynamic api keys, helping in fixing isuues
I mean genral use, and how to make ai assistant remeber it each time (permanent) 
give me very simple tools free and reliable valid working, to allow ai screen link for web app to test and dicover errors (do not tell me playwrite or mcp )

Architecting Intelligence: A Comprehensive Framework for Deterministic, AI-Augmented Web DevelopmentExecutive SummaryThe discipline of software engineering is currently navigating a precipitous phase shift, moving from a syntax-centric paradigm—where the developer’s primary cognitive load is translating logic into specific language constructs—to an intent-centric model. In this emerging era, the developer acts less as a mason laying individual bricks and more as an architect and orchestrator, while Artificial Intelligence (AI) serves as the implementation engine. This transition, however, is fraught with complexity. Large Language Models (LLMs) are, by definition, probabilistic engines designed to predict the next token based on statistical likelihood, not deterministic logic gates grounded in absolute truth. Consequently, they are prone to hallucinations, logic drift, security oversights, and "confident incompetence."To achieve results that are "powerful and successful" from the first attempt, where AI does not repeat errors and produces valid, testable code, developers must abandon the casual "chatbot" interaction model. Instead, they must adopt rigorous engineering frameworks that constrain the probabilistic nature of AI into deterministic outputs. This report provides an exhaustive analysis of the methodologies required to achieve this transformation. It details advanced prompt engineering frameworks such as Chain of Thought (CoT) and Tree of Thoughts (ToT), the integration of Test-Driven Development (TDD) as a non-negotiable validity constraint, the strategic orchestration of free-tier intelligent tools like Cursor and Bolt.new, and the mitigation of common AI-induced vulnerabilities in modern frameworks like Next.js 15. By synthesizing these elements, we establish a protocol for "Zero-Error" AI development.Chapter 1: Cognitive Architectures for Deterministic Code GenerationThe distinction between a novice obtaining broken, hallucinated code and an expert generating production-ready systems lies almost entirely in the application of cognitive architectures. An LLM does not "know" how to code in the human sense; it approximates reasoning through high-dimensional vector associations. To force the model to reason correctly, one must structure the input to mimic robust human problem-solving strategies, effectively creating a "cognitive scaffolding" that supports the weight of complex logic.1.1 The Chain of Thought (CoT) ProtocolChain of Thought (CoT) represents the foundational technique for eliciting complex reasoning from Large Language Models. In standard, zero-shot prompting, a user asks for an answer, and the model attempts to jump directly from the question to the solution. For complex tasks involving multi-step reasoning—such as web development architecture—this direct leap often results in logic gaps. CoT facilitates problem-solving by guiding the model through a coherent series of intermediate logical steps, effectively allowing the model to "think out loud" before committing to a final output.11.1.1 The Mechanism of CoT ReasoningThe mechanism of CoT relies on breaking the probabilistic dependency between the initial prompt and the final code block. Research indicates that prompting models to generate intermediate reasoning steps significantly boosts their ability to accurately solve multistep problems, including symbolic reasoning and algorithmic logic.1 When a model generates a reasoning step (e.g., "First, I need to define the database schema because the frontend depends on the data structure"), it adds new tokens to its context window. These tokens then serve as a grounded input for the subsequent generation steps, reducing the "search space" for the next token and increasing the probability of a correct result.2This phenomenon is described as an "emergent ability," meaning it appears and becomes effective only as the model size and complexity scale up.1 For web development, this means that CoT is particularly effective when using larger reasoning models (like GPT-4o or Claude 3.5 Sonnet) compared to smaller, quantized local models.1.1.2 Zero-Shot vs. Few-Shot CoTThere are two primary implementations of CoT that developers must master:Zero-Shot CoT: This is achieved by simply appending the phrase "Let's think step by step" to the prompt. This trigger forces the model to decompose the problem without needing specific examples.2Few-Shot CoT: This involves providing the model with "exemplars"—examples of a question, a step-by-step reasoning process, and the final answer.1 For a developer, this might look like providing a snippet of a React component, explaining the prop drilling logic, and then showing the final code.1.1.3 Advanced CoT Prompt Template for Web ArchitectureTo ensure the AI "understands" the architectural requirements before writing a single line of syntax, the following framework should be employed. This structure leverages the "Plan-then-Execute" pattern, which is a derivative of CoT.3System Instruction:"You are a Principal Software Engineer. Do not output code immediately. You must first engage in a 'Architectural Reasoning Phase'. Break down the user's request into logical components, data flow requirements, and edge cases. Only after you have explicitly written out this plan step-by-step should you generate the implementation."User Prompt Structure:Context: "I am building a Next.js 15 application using the App Router and React Server Components."Task: "Create a multi-step user registration wizard."Constraint: "Use Tailwind CSS for styling, Zod for server-side validation, and ensuring accessibility compliance (WCAG 2.1)."CoT Trigger: "Let's think step by step. First, define the Zod schema for each step. Second, outline the client-side state management strategy. Third, identify necessary server actions for the final submission. Finally, generate the code."By forcing this linearization of thought, the developer prevents the model from rushing into writing a React component before it has decided on the underlying data structure.1.2 Tree of Thoughts (ToT): Exploring the Solution SpaceWhile CoT is linear, complex web development problems often require non-linear exploration. A linear path is insufficient when there are multiple viable architectural patterns (e.g., deciding between Redux, Zustand, or React Context for state management). The Tree of Thoughts (ToT) framework generalizes CoT by allowing the model to explore multiple reasoning paths simultaneously, self-evaluate them, and backtrack if a path is suboptimal.41.2.1 ToT for Architectural DecisionsThe operational dynamics of the ToT framework involve an iterative, tree-structured exploration of possible solutions. Starting with the initial prompt, the model generates a range of "thoughts" or options, each leading to subsequent branches. It employs self-evaluation to ensure each step's validity before proceeding.5The ToT Prompt Strategy:To implement ToT without writing custom Python scripts, one can simulate the process via a structured prompt:"Imagine three different experts are discussing how to implement authentication for this application.Expert A advocates for a custom JWT implementation using generic libraries.Expert B advocates for Auth.js (NextAuth) for its ecosystem integration.Expert C advocates for a managed service like Clerk or Supabase Auth to minimize maintenance.Have each expert present their argument, specifically critiquing the others based on security risks, implementation speed, and long-term maintenance. After the debate, synthesize the discussion and recommend the optimal path for a solo developer with a zero-budget constraint."This prompts the model to simulate a "tree" of possibilities. By evaluating the state of each branch (e.g., realizing that Custom JWT has high security risks), the model avoids the "first plausible answer" bias common in standard prompting.5 This mirrors the human ability to navigate a maze of options, reassessing strategies as needed.1.3 The Persona-Based System Prompt and Role PromptingOne of the most effective ways to improve code quality is to constrain the AI's "personality." A generic model tries to be helpful and agreeable; a specific persona adopts the heuristics, strictness, and biases of a domain expert.6 This technique, known as Role Prompting, fundamentally changes how the model processes and responds to requests by narrowing the probabilistic search space to tokens associated with high-expertise literature.61.3.1 The "Senior Architect" PersonaTo prevent the generation of "tutorial-level" code (which is often insecure, unoptimized, or simplistic), the system prompt must define a high level of seniority and specific behavioral boundaries.Master System Prompt Template:"You are an expert Full-Stack Web Developer with 15+ years of experience in high-scale distributed systems. You prioritize security, type safety (TypeScript), and maintainability over brevity.Rules of Engagement:No Yapping: Do not provide conversational filler. Focus on technical density. If the code speaks for itself, provide minimal commentary.7Security First: Always validate inputs (Zod/Yup) and sanitize outputs. Never hardcode secrets or suggest insecure defaults.8Modern Standards: Use modern syntax (e.g., React Server Components, ES6+ modules). Avoid legacy patterns (e.g., var, Class components) unless explicitly requested.Error Handling: Every asynchronous operation must be wrapped in error handling (try/catch or error boundaries).Self-Correction: If you identify a potential flaw or ambiguity in the user's request, explicitly state it and ask for clarification before coding.9"This prompt sets the "temperature" of the interaction, reducing the likelihood of naive errors by anchoring the model's output distribution to professional-grade code repositories.101.4 Meta-Prompting: The Self-Optimization LoopMeta-prompting is an advanced technique where the AI is used to generate or optimize its own prompts. It treats the prompt as a programmable object. Empirical experiments have shown that meta-prompting can enable models to surpass supervised fine-tuned counterparts on complex tasks.11Implementation:If a developer is struggling to get the AI to generate a specific CSS layout, they can use a meta-prompt:"I want to generate a complex grid layout using Tailwind CSS, but my prompts are resulting in broken responsiveness. Act as a Prompt Engineering Expert. Analyze the requirements for a 'bento-box style dashboard' and write the perfect prompt that I should feed back to you to get the correct code."This recursive process allows the developer to leverage the model's internal knowledge of how it interprets instructions, effectively aligning the user's intent with the model's capabilities.12FrameworkCore MechanismBest Use Case in Web DevComplexityChain of Thought (CoT)Step-by-step linear reasoning.Component logic, API integration flows.LowTree of Thoughts (ToT)Branching exploration of multiple solutions.Architecture selection (DB choice, Stack choice).HighRole PromptingAdopting a specific expert persona.Enforcing code quality, security standards.LowMeta-PromptingAI writing/optimizing its own prompts.Debugging failed prompts, complex creative tasks.MediumChapter 2: The Zero-Error Protocol: Test-Driven Development (TDD) with AIThe user query explicitly asks for a method to "ensure each step works" and gives a "hundred percent true result." In the domain of software engineering, the only mechanism that approaches this guarantee is automated testing. When combined with AI, Test-Driven Development (TDD) transforms from a tedious chore into a powerful verification loop.142.1 The TDD-LLM LoopStandard usage of LLMs involves generating code and then testing it manually—a "Test-Last" approach that is prone to subtle bugs. The TDD-LLM loop reverses this flow. By forcing the AI to define the "Truth" (the test) before the "Solution" (the code), the developer creates a rigid constraint that the implementation must satisfy.Research utilizing benchmarks like WebApp1K has demonstrated that LLMs perform significantly better when the prompt includes specific test cases they must satisfy, or when they are tasked with writing the tests themselves.14 This methodology aligns with the "Plan-then-Execute" strategy but adds a layer of executable verification.The Protocol:Prompt for Tests: Ask the AI to write the test case first, based on the feature requirements.Verify Tests: The human developer reviews the test logic. This is crucial; checking that a test accurately describes a feature is often cognitively easier than reviewing the implementation logic.Generate Code: Ask the AI to write code specifically to pass the generated test.Iterate: Run the test. If it fails, feed the error message back to the AI (Self-Correction).2.2 Detailed TDD Prompting StrategyPhase 1: The Specification and Test Generation"We are adopting a Test-Driven Development approach. I need to implement a 'Shopping Cart' class.Requirements:Add items with ID, price, and quantity.Remove items by ID.Calculate total price (including tax).Apply discount codes (percentage based).Task: Create a comprehensive test suite using Vitest. Cover the 'Happy Path' and at least 3 edge cases (e.g., negative quantity, invalid discount code). Output ONLY the test file."Phase 2: The Implementation"Now, write the TypeScript implementation for the ShoppingCart class. The code must pass exactly the tests you just wrote. Do not add any features not covered by the tests. Ensure strict type safety."Phase 3: The Self-Correction Loop (The 'Refactor' Step)If the code fails the test, the error message becomes the next prompt. This is where AI shines—debugging based on explicit feedback."The code failed the test 'calculates subtotal correctly'.Error: Expected 50, Received 45.Analyze the logic error in the calculation function. Explain why it failed, then output the corrected code block."This creates a "Self-Correcting Code Generation" pipeline. Recent "Agentic" frameworks like smolagents or OpenHands are attempting to automate this loop entirely, where the agent writes code, runs the test command, reads the terminal output, and iterates without human intervention until the test passes.162.3 Ensuring Validity: The "No Yapping" ConstraintWhen performing TDD with AI, verbosity is an enemy. Excess text in the response ("Here is your code", "I hope this helps") dilutes the context window and can confuse parsing tools. A highly effective prompt instruction is "No yapping" or "Output code only.""You are a recipe tweet generator... just the ingredients, no yapping.".7While humorous, this constraint forces the model to focus its probability distribution solely on the structural output (the code/test), often resulting in higher accuracy and adherence to formatting rules.Chapter 3: The Integrated Toolchain: Orchestrating Free and Intelligent AgentsTo "think better and see the result," developers need tools that integrate AI directly into the workflow. The landscape in 2025 has evolved from simple chat interfaces to comprehensive "AI Editors" and "Vibe Coding" environments. The user specifically asks for "free intelligent tools" and how they help code functionality.3.1 The AI Code Editor Landscape3.1.1 Cursor: The Context-Aware OrchestratorCursor is currently widely regarded as the premier AI code editor. It is a fork of VS Code, meaning it supports all VS Code extensions, but integrates AI at the core rather than as a plugin.17Key Feature: "Tab" Autocomplete: Unlike standard autocomplete, Cursor's "Tab" predicts entire blocks of code and edits based on the surrounding context. It uses a "Fill-in-the-middle" objective, allowing it to edit code around your cursor, not just append to it.Key Feature: Composer (CMD+I): This allows for multi-file editing. A developer can ask Cursor to "Refactor the authentication flow" and it will simultaneously modify the frontend components, the backend API routes, and the database schema files.Free Tier Analysis (2025):Cursor's pricing model has shifted from simple request limits to "usage-based credit pools".18Hobby Plan (Free): typically includes a generous but finite access to premium models (like Claude 3.5 Sonnet or GPT-4o). It usually includes a two-week trial of "Pro" features.Limits: Once the "fast premium" requests are exhausted (often around 500 requests or a specific token cap), the user may be downgraded to "slow" requests or basic models.20Strategy: Use the initial trial period for heavy architectural lifting. For ongoing maintenance, the basic models or "slow" requests are often sufficient for single-file edits.3.1.2 Bolt.new: The Browser-Based Full-Stack BuilderBolt.new represents a newer category often called "Vibe Coding" or instant prototyping. It differs from Cursor in that it runs an entire development environment (Node.js, WebContainer) inside the browser.22Capability: A user can prompt "Build a Trello clone with drag-and-drop" and Bolt will scaffold the project, install dependencies (npm/pnpm), run the dev server, and render the preview—all in one browser window.Free Tier Limitations:Bolt.new uses a Token Limit system. Free plans typically have a daily limit (e.g., 150k - 300k tokens) and a monthly cap (e.g., 1 million tokens).23Constraint: Large projects consume tokens rapidly because the AI has to "read" the entire file structure to maintain context.Optimal Workflow: Use Bolt.new for the start of a project (the first hour) to get a working skeleton. Then, export the code to a local environment (VS Code/Cursor) to avoid hitting the token wall.3.1.3 Windsurf and QodoWindsurf: A direct competitor to Cursor, focusing on "Flow" states. It creates a deep context awareness of the codebase, similar to Cursor's "Context" features.27Qodo (formerly Codium): This tool focuses on code integrity and quality rather than just generation. It integrates into IDEs to provide agentic code review, test coverage analysis, and compliance checks.28 It is particularly useful for the "valid test" requirement in the user query.3.2 Visualization Tools for "Thinking Better"The user asks for tools to "see the result and code functionality better." Textual code is abstract; visual representation reduces cognitive load and helps identify logic errors before execution.ToolFunctionFree Tier StatusIntegrationBest ForMermaid.jsText-to-Diagram generation.Open Source / Free 29Native in GitHub/Notion. Plugins for VS Code.Generating flowcharts and sequence diagrams directly from the LLM to visualize logic flow.GraphvizStructural visualization.Open Source 30Command Line / VS Code Plugins.Visualizing complex database schemas or dependency graphs.ExcalidrawHand-drawn style diagramming.Free / Open SourceWeb / VS Code Extension.Sketching high-level architecture and UI wireframes.WarpAI-enhanced Terminal.Free for individuals 8Desktop App.Understanding command line errors. It uses AI to explain stderr outputs in plain English.Workflow for Visualization:Paste a complex function or API route into the LLM.Prompt: "Generate a Mermaid.js sequence diagram that explains the data flow in this function, specifically highlighting the error handling paths."Paste the code into the Mermaid Live Editor or view it directly in a markdown previewer.29 This allows the developer to "see" logic gaps (e.g., a missing arrow in the error flow) immediately.3.3 The Free "Intelligent" Tool Combination StrategyTo maximize power without incurring subscription costs, a developer should combine these tools into a pipeline:Ideation & Architecture: Use ChatGPT (Free Tier) or Claude (Free Tier) to perform high-level Chain of Thought planning.Scaffolding (The "First Time" Build): Use Bolt.new (Free Tier) to prompt the initial application structure. Let it handle the complex configuration of package.json, tsconfig.json, and basic routing.Development & Refinement: Export the project to VS Code equipped with the Cursor (Hobby) or Qodo extension. Use Cursor for code completion and refactoring. Use Qodo to generate tests.Visualization: Use Mermaid.js prompts within the chat to visualize complex logic as you build.Chapter 4: The Pathology of AI Errors: Common Mistakes and MitigationThe user specifically asks about "common mistakes between ai models" so they can be avoided. AI errors are not random; they are structural and stem from the nature of their training data and architecture.4.1 The Hallucination of Dependencies (Supply Chain Risks)AI models, having been trained on vast repositories of open-source code, often suggest importing packages that sound plausible but do not actually exist. This phenomenon is exploited by attackers in a technique called "slopsquatting" or "dependency confusion".31 An attacker might notice that AI frequently hallucinates a package named react-secure-input and then register that exact name on npm with malicious code.The Mistake: Blindly running npm install <suggested-package> or pip install <suggested-package> without verification.The Fix: Always verify that a package exists on the official registry (npm, PyPI) and has a history of maintenance and downloads.The Prompt Constraint: "Only use standard, well-maintained libraries (e.g., those with >10k weekly downloads). If a specific library is needed, verify its existence or suggest a standard alternative."4.2 Framework-Specific Hallucinations (The Next.js Transition)AI training data has a "knowledge cutoff." Models often confuse older architectural patterns with newer ones, particularly in rapidly evolving frameworks like Next.js. A common error is mixing Pages Router (Next.js 12/13) patterns with App Router (Next.js 13/14/15) patterns.32Common Errors:Client/Server Confusion: Attempting to use useState or useEffect (Client-side hooks) inside a Server Component without the "use client" directive. This leads to immediate runtime errors.32Data Fetching: Fetching data inside a useEffect hook when it should be a direct async/await call in a Server Component.Route Handlers: Using the old API route syntax (export default function handler(req, res)) instead of the new Route Handler syntax (export async function GET(request)).The Fix: Explicitly version-stamp the prompt. "You are an expert in Next.js 15. Do not use the Pages router. Prioritize React Server Components. Do not use useEffect for data fetching unless strictly necessary for client interaction."4.3 Security Blind Spots and Insecure DefaultsAI generates code that functions but is often insecure. It prioritizes brevity and functionality over security rigor. Research shows that AI-generated code frequently contains vulnerabilities like SQL Injection, XSS (Cross-Site Scripting), and IDOR (Insecure Direct Object References) because generic training data often omits complex validation logic for readability.8The Mistake: Accepting raw user input in database queries (e.g., const user = db.query("SELECT * FROM users WHERE id = " + req.body.id)).The Fix: Use a "Security Auditor" persona prompt after generation."Review the code you just wrote as a Senior Security Engineer. Identify potential IDOR, XSS, or Injection vulnerabilities. Rewrite the code to be secure by default, using parameterized queries and input validation."4.4 Context Window Overflow (The "Goldfish Memory" Effect)As a conversation with an AI extends over many turns, the model "forgets" early instructions as they slide out of its context window. It might revert to using vanilla CSS after being told to use Tailwind, or forget the TDD constraint entirely.38The Mistake: Assuming the AI remembers the "System Prompt" from 50 messages ago.The Fix:Repo Context: Use tools like Cursor that index the codebase (@Codebase), allowing the AI to retrieve context dynamically rather than relying on chat history.Refresher Prompts: Every 10-15 turns, restate the core constraints. "Reminder: We are using TypeScript Strict Mode and Tailwind CSS."Convention Files: Maintain a CONVENTIONS.md file in your project root. Instruct the AI to "Read CONVENTIONS.md before generating any code".38Chapter 5: Computational Creativity: Thinking Out of the BoxThe user requests prompts to make AI "think out of box and more creative." LLMs are statistical averages; they tend to converge on the most probable (and therefore most generic) solution. To generate novel web designs or solutions, we must disrupt this convergence.5.1 The SCAMPER FrameworkSCAMPER is a classic lateral thinking technique that can be encoded into prompts to force novel solutions. It stands for Substitute, Combine, Adapt, Modify, Put to another use, Eliminate, and Reverse.39S - Substitute: "What if we substituted the standard navigation bar with a voice-controlled command palette?"C - Combine: "Combine the concept of a 'Shopping Cart' with a 'Tinder-like swipe interface' for selecting products."A - Adapt: "Adapt the user onboarding flow from a video game (e.g., a tutorial level) for this finance app."M - Modify: "Magnify the micro-interactions. Make the buttons react physically to the cursor velocity."P - Put to another use: "How can the 404 error page be used to generate leads or entertain the user?"E - Eliminate: "Eliminate the login screen entirely. How do we authenticate?" (This prompts ideas like magic links, biometrics, or device-based auth).42R - Reverse: "Reverse the data flow. Instead of the user searching for products, the products search for the user based on their profile."The SCAMPER Prompt:"I need a creative UI for a task management app. The standard list view is too generic. Apply the SCAMPER framework to the standard 'To-Do List' interface. Specifically focus on 'Modify', 'Combine', and 'Reverse'. Generate 3 radical design concepts that defy standard conventions.".435.2 Role-Playing for Design InnovationBy asking the AI to assume the persona of a specific design movement or a famous designer, you shift the probability distribution of its output toward that specific style, avoiding the "Bootstrap/Material Design" average.Prompt: "Design the landing page as if you were a proponent of Brutalism (Web Design). Use high contrast, raw typography, visible grid lines, and unpolished aesthetics."Prompt: "Design the interface using Glassmorphism principles. Focus on translucency, background blur, and floating layers.".45Chapter 6: The Master Reference: Prompt LibraryThis section consolidates the insights into copy-pasteable templates designed to meet the user's request for "powerful," "intelligent," and "creative" prompts.6.1 The "Genesis" Prompt (Project Setup)Use this to start a project correctly, ensuring architecture is sound before code is written."Act as a Senior Solutions Architect. We are building [Project Name].Tech Stack: Next.js 15 (App Router), Tailwind CSS, Supabase, TypeScript.Goal:.Phase 1: Architecture & ReasoningDo not write code yet.Schema: Define the database schema (SQL) and relationships.Structure: Outline the folder structure following App Router conventions.API: List the necessary API endpoints and Server Actions.Conventions: Create a CONVENTIONS.md file listing the coding standards (e.g., 'Always use Zod for validation', 'Prefer Server Components').Review this architecture for scalability and security flaws. Once I approve this plan, we will move to implementation."6.2 The "TDD Implementer" Prompt (The Loop)Use this to ensure valid code and prevent errors."We are implementing the [Feature Name] using Test-Driven Development.Write the Test: Create a robust test file using Vitest/Jest that covers the happy path, error states, and edge cases (e.g., empty inputs, network failure).Halt: Stop and wait for my confirmation that the test looks correct.Implement: Once confirmed, write the minimal code required to pass these tests.Refactor: If the tests pass, refactor the code for readability without breaking the tests.".466.3 The "Bug Fixer" Prompt (Chain of Thought)Use this when things break to find the root cause."The following code is throwing Error: [Error Message].Code: [Paste Code].Task:Analyze: Explain the causal chain that leads to this error. Trace the data flow step-by-step.Hypothesize: Propose 3 potential root causes.Verify: Which hypothesis is most likely?Fix: Provide the corrected code and explain exactly why this fixes the issue.Prevent: How do we ensure this doesn't happen again?"6.4 The "Creative Spark" PromptUse this for design blocks to think out of the box."I am stuck on the design for the [Component]. It feels generic.Task:Generate 4 distinct UI variations based on the following concepts:Minimalist: (Apple-esque, whitespace, typography-driven).Playful: (Duolingo-esque, gamified, bouncy animations).Data-Dense: (Bloomberg Terminal, high information density).Radical: (Apply the 'Reverse' principle from SCAMPER).For each, describe the layout, color palette, and interaction model. Then, provide the Tailwind classes for the best option.".39ConclusionAchieving "hundred percent true results" with AI in web development is an asymptotic goal—one approaches it but never fully touches it due to the inherent probabilistic nature of Large Language Models. However, by layering deterministic frameworks (TDD, Schema Validation, Strict Typing) over probabilistic generation (LLMs), developers can achieve a level of reliability that feels like "intelligence."The successful AI developer in 2025 is not a prompt typist, but a system architect. They use Chain of Thought to force reasoning, TDD to force validity, Cursor/Bolt to accelerate implementation, and SCAMPER to inject creativity. They treat the AI not as a magic wand, but as a high-speed, slightly unreliable junior partner that requires precise instruction (Prompts), constant supervision (Tests), and the right tools (Environment) to succeed. By adopting the "Senior Architect" persona and enforcing the "Zero-Error Protocol" defined in this report, the developer transforms the AI from a chatty assistant into a rigorous, powerful coding engine.
QuickTake
Use free tools like Cursor, Bolt.new, Mermaid.js, Graphviz, and Excalidraw for web app testing and error discovery.








Model's thoughts
Universal AI Development Prompt Template
Copy-paste ready for any web development task

Master System Prompt (Save this in your notes/bookmark)
You are an expert Full-Stack Developer with 15+ years experience. Follow these rules:

THINKING PROCESS:
1. First, explain your approach step-by-step before coding
2. Identify potential issues and edge cases
3. Choose the best solution from multiple options
4. Only then write the implementation

CODE STANDARDS:
- TypeScript/JavaScript: Use modern ES6+, async/await, proper error handling
- Security: Always validate inputs, sanitize outputs, never expose secrets
- Testing: Write tests first (TDD approach) when possible
- Comments: Only when logic is complex, let code self-document

OUTPUT FORMAT:
- No unnecessary chat, get straight to the solution
- Use ```language blocks for all code
- If multiple files, clearly label each with // filename.ext
- Include installation commands if external packages needed

SELF-CORRECTION:
- If you spot an error in your response, immediately correct it
- If requirements are unclear, ask for clarification
- Always consider: "What could break this?"
Task-Specific Templates
1. Web App Builder
Create a [APP TYPE] with these requirements:
- Tech Stack: [React/Next.js/Vue] + [Database] + [Styling]
- Features: [List main features]
- Constraints: [Budget/Time/Hosting limits]

Step 1: Design the data structure/schema
Step 2: Plan the component hierarchy  
Step 3: Define API endpoints needed
Step 4: Write implementation with tests
2. PDF to Exam Generator
Convert this PDF content to an interactive quiz/exam:
- Input: [PDF text or key concepts]
- Output: JSON structure with questions, answers, scoring
- Types: Multiple choice, true/false, fill-in-blank
- Include: Answer key, explanation for each answer
- Format: {questions: [], answers: [], scoring: {}}
3. Debug/Fix Issues
Debug this error:
Error Message: [paste error]
Code: [paste relevant code]
Context: [what were you trying to do]

Analyze using Chain of Thought:
1. What is the error literally saying?
2. Trace the execution path
3. Identify the root cause
4. Provide fixed code
5. Explain how to prevent this
How to Make AI Remember (Permanent Memory)
Free & Simple Solutions:
Custom Instructions (ChatGPT)
Go to Settings → Personalization → Custom Instructions
Paste your master prompt there
It applies to all future conversations
Project Files Method
Create these files in your project root:
- AI_RULES.md (your prompts/standards)
- CONTEXT.md (project specifics)
- CONVENTIONS.md (coding standards)

Start each session with: "Read AI_RULES.md, CONTEXT.md before responding"
Browser Bookmarklet
javascript

Download

Copy code
javascript:(function(){
  const prompt = `[YOUR MASTER PROMPT HERE]`;
  navigator.clipboard.writeText(prompt);
  alert('Prompt copied to clipboard!');
})();
Save as bookmark, click to copy your prompt instantly
Text Expander (Free alternatives)
Windows: AutoHotkey (create shortcut like ::aiprompt:: to expand full prompt)
Mac: Built-in Text Replacements (Settings → Keyboard → Text)
Chrome: Text Blaze extension (free tier available)
Free Tools for Web App Testing & Error Discovery
1. Browser-Based Testing (No Installation)
StackBlitz

Full VS Code in browser
Live preview with console
Share link for AI to analyze
Free for public projects
CodeSandbox

Instant dev environment
Real-time error detection
Browser DevTools integration
Shareable URLs for debugging
Replit

Full-stack hosting included
Built-in debugger
AI can access via public URLs
Free tier with limitations
2. Error Detection Tools
Browser DevTools Method

javascript

Download

Copy code
// Paste in console to capture all errors
window.addEventListener('error', (e) => {
  console.log('Error captured:', {
    message: e.message,
    source: e.filename,
    line: e.lineno,
    column: e.colno,
    error: e.error
  });
});
JSFiddle or CodePen

Instant HTML/CSS/JS testing
Console output visible
Share link with AI for analysis
3. Visual Testing (Screenshots for AI)
Responsively App (Free, Open Source)

See all screen sizes simultaneously
Take screenshots of errors
Built-in device emulation
Chrome Extension: GoFullPage

Capture entire page screenshot
Share with AI for visual debugging
4. API Testing
Hoppscotch (Free, Open Source)

Browser-based API testing
No installation needed
Share request/response with AI
Quick Start Workflow
Setup Phase:
I need a [project type]. Using the Chain of Thought method:
1. List assumptions and clarify requirements
2. Design the architecture
3. Choose the tech stack
4. Plan the implementation steps
Then create the initial code structure.
Development Phase:
Implement [feature] following TDD:
1. Write the test cases first
2. Show me the tests for review
3. Write code to pass the tests
4. Refactor if needed
Debug Phase:
Error occurred: [paste error]
URL: [StackBlitz/CodeSandbox link]

Diagnose using:
1. Error message analysis
2. Code flow tracing
3. Fix implementation
4. Prevention strategy
Power Tips
For Better Results:
Always include: "Think step-by-step before coding"
Specify versions: "Using React 18, Next.js 15"
Add constraints: "Explain for a beginner" or "Production-ready code only"
For Creativity:
"Give me 3 unconventional approaches to..."
"Apply SCAMPER method to this UI design"
"Design this as if [famous company] built it"
For Accuracy:
"Double-check your solution for errors"
"What edge cases am I missing?"
"Rate this solution's security from 1-10 and explain"
Save this entire document as AI_ASSISTANT_GUIDE.md in your projects or bookmark it for instant access!


I prefer this








Model's thoughts
Here is a comprehensive solution designed to meet your specific requirements: a "permanent" memory setup, a copy-paste Master Prompt for Full-Stack development (specifically handling PDF-to-App and JSON-to-API workflows), and simple free tools for testing.

Part 1: How to make the AI "Remember" (Permanent Memory)
To avoid pasting this huge prompt every time, you must use the "Custom Instructions" or "System Prompt" feature available in most advanced AI tools.

ChatGPT: Click your Name 
→
→ Custom Instructions 
→
→ Paste the prompt below into the "How would you like ChatGPT to respond?" box.
Claude (Pro): Create a "Project" and paste this into the "Project Instructions."
General Use: If you don't have those features, save this text in a text file (e.g., MASTER_PROMPT.txt). Paste it as the very first message of every new chat session.
Part 2: The Master Copy-Paste Prompt
Copy the text inside the code block below. It is engineered based on the "Architecting Intelligence" principles you provided, specifically tuned for converting PDFs/JSON into functional Web Apps with dynamic API handling.

markdown

Download

Copy code
# MASTER SYSTEM PROMPT: Full-Stack Architect & Error-Free Protocol

**ROLE:**
You are a Principal Software Engineer and Systems Architect. You do not act as a chatbot; you act as a rigorous coding engine. Your goal is "Zero-Error" execution using Chain of Thought (CoT) and Test-Driven Development (TDD).

**CORE DIRECTIVES:**
1.  **No Yapping:** Do not offer conversational filler. Output plans, reasoning, or code only.
2.  **Security First:** Always sanitize inputs. Never hardcode API keys; use Dynamic Environment Variable injection.
3.  **Modern Stack:** Unless told otherwise, use React/Next.js (Frontend), Node/Express or Python/FastAPI (Backend), and Tailwind CSS.
4.  **Validation:** Use strict schema validation (Zod/Pydantic) for all data.

**MANDATORY WORKFLOW (Follow this for every request):**

**PHASE 1: ANALYSIS & DECONSTRUCTION**
*   If User inputs a PDF/Text Content: Extract the raw data structure. Convert this immediately into a clean JSON schema.
*   If User inputs JSON: Analyze the key-value pairs to determine necessary API endpoints.
*   **Output:** A detailed "Architectural Blueprint" listing the Database Schema, API Routes, and Frontend Component hierarchy. *Wait for user approval before coding.*

**PHASE 2: JSON TO DYNAMIC API STRATEGY**
*   When handling JSON data that requires API fetch:
    *   Do NOT write static fetch calls.
    *   Create a "Dynamic Handler" that accepts JSON keys as parameters.
    *   Store all API Keys in a `.env` structure (e.g., `REACT_APP_API_KEY`).
    *   Write a secure middleware function to rotate or call these keys dynamically.

**PHASE 3: TEST-DRIVEN DEVELOPMENT (TDD)**
*   Before writing the App code, write the **TEST** first.
*   Create a unit test (Jest/Vitest) that validates the JSON parsing and API response.
*   **Constraint:** The code you generate in Phase 4 MUST pass the test generated here.

**PHASE 4: IMPLEMENTATION**
*   Generate the Backend code (API/Server).
*   Generate the Frontend code (UI/Display).
*   Ensure strict typing (TypeScript interfaces based on the initial JSON).

**PHASE 5: ERROR DISCOVERY & SELF-CORRECTION**
*   If the user provides an error log or screen link data:
    *   Analyze the Trace.
    *   Identify the "Root Cause" (not just the symptom).
    *   Apply the fix and generate a new Regression Test to ensure it doesn't happen again.

**USER INPUT:**
[The user will paste their request, PDF content, or JSON here]
Part 3: How to use this for your specific needs
Here is how to use the prompt above to solve your specific problems:

1. Converting PDF Exams to Web App
Step 1: Activate the Master Prompt.
Step 2: Copy the text from your PDF (or upload the PDF if the AI supports file reading).
Step 3: Type: "Convert this PDF content into a JSON structure for a quiz app, then build the Next.js frontend to render it."
Result: The AI will first create the JSON (Question/Answer format), then write the code to dynamically render that JSON.
2. Converting JSON to Dynamic API Keys
Step 1: Paste your JSON data.
Step 2: Type: "Map this JSON data to external API endpoints. Create a backend service that uses dynamic API keys from a .env file to fetch data for each ID in this JSON."
Result: The AI will generate a backend proxy that hides your API keys from the frontend, securing your app.
Part 4: Simple, Free Tools for "Screen Linking" and Error Discovery
You asked for valid, working tools to "screen link" (test a live URL) and discover errors without using complex code like Playwright.

1. Google Lighthouse (The Standard)

What it is: Built directly into Chrome. No installation needed.
How to use:
Open your web app/link in Chrome.
Press F12 (or Right Click -> Inspect).
Click the "Lighthouse" tab.
Click "Analyze page load".
Why for AI: It generates a report of Accessibility, SEO, and Performance errors. Copy the text from the "Issues" list and paste it into the AI with the command: "Fix these Lighthouse errors."
2. The W3C Markup Validator (For Structural Integrity)

What it is: A free website run by the people who make the web standards.
Link: validator.w3.org
How to use: Paste your Web App URL.
Why for AI: It finds broken HTML tags that break your UI. Copy the error list and paste to AI: "Correct my HTML based on these W3C errors."
3. Checkbot (Chrome Extension)

What it is: A free browser extension.
How to use: Click the button, and it crawls your site.
Why for AI: It specifically checks for Broken Links (404s), duplicate titles, and insecure forms. It handles the "Discovery" part automatically.
4. Postman (Free Tier - For API/Backend)

What it is: A tool to test your Backend logic/JSON before connecting the Frontend.
How to use: Send your JSON data to your API URL.
Why for AI: If you get an error (e.g., 500 Internal Server Error), copy the Response Body from Postman and paste it to the AI. This allows the AI to fix the backend logic immediately.
Summary Workflow:

Build using the Master Prompt.
Run the app.
Scan using Lighthouse (F12).
Paste Lighthouse errors back to the AI to auto-fix.

I prefer this







Here’s a clean, ready-to-copy-paste prompt designed for general use in any web app — whether you're building exams from PDFs, converting JSON to dynamic API keys, fixing bugs, or generating full-stack code. It’s optimized for free, reliable, non-Playwright/MCP tools, includes permanent memory tricks, and lets you test AI-generated UIs live with simple, valid tools.

✅ Copy-Paste Prompt: AI Web Developer Assistant (General Use)
You are a Senior Full-Stack Developer with 15+ years of experience. You write production-ready, secure, and maintainable code. You never guess. You always think step-by-step.

Rules:
- NO yapping. No fluff. No explanations unless asked.
- Use TypeScript, React Server Components (Next.js 15 App Router), Tailwind CSS, Zod for validation.
- Never use legacy patterns (Class components, var, Pages Router).
- Always validate inputs. Never hardcode secrets.
- If unsure, ask for clarification before coding.
- If code fails, debug using error messages — don’t guess.

Your task: [Insert your request here — e.g., “Convert this PDF exam into a web-based quiz with timer and score tracking,” or “Generate dynamic API keys from this JSON config and serve them via a secure Next.js endpoint,” or “Fix this error: [paste error]”]

Step 1: Plan
Break this into: 
- Data flow (what inputs/outputs?)
- Required components (frontend/backend)
- Security risks (XSS, injection, key leaks?)
- Edge cases (empty PDF, invalid JSON, network failure)

Step 2: Build
Only after I approve the plan, generate:
- Folder structure
- Code files (one at a time if large)
- Test cases (Vitest) if it’s logic-heavy

Step 3: Test
If something breaks:
- Paste the exact error
- I’ll tell you to fix it
- You’ll debug using Chain of Thought: “Analyze → Hypothesize → Fix → Prevent”

Tools I use (free & reliable):
- For live preview: https://bolt.new (paste code here to test instantly)
- For diagrams: Paste code → ask “Generate Mermaid.js diagram of this flow”
- For debugging: Use https://warp.dev (free AI terminal — paste stderr to understand errors)
- For permanent memory: I will paste this entire prompt at the start of every conversation. You must remember it forever.

Do not suggest npm packages unless they have >10k weekly downloads and are on npmjs.com.
Do not use useEffect for data fetching in Server Components.
Never assume. Always verify.
🔁 How to Make AI Remember This Forever (Permanent Memory)
✅ Simple, free, and works on any AI platform (ChatGPT, Claude, Gemini, etc.)

➤ Method: Save as a “System Prompt Template” in Your Notes
Save this entire prompt in a text file or note app (e.g., Notion, Obsidian, Apple Notes, Google Keep).
Before every new question, copy and paste this prompt first.
Then add your request:
Now, here’s my task: [your task]
💡 Why this works: AI doesn’t have memory between chats — but you control the input. By pasting this every time, you’re giving it the context it needs to behave like a senior dev. It’s not magic — it’s prompt hygiene.

🚫 Don’t rely on “memory” features — they’re unreliable. You are the memory.

🛠️ Free, Reliable Tools to Test AI-Generated Web Apps (No Playwright, No MCP)
Tool	Use Case	Link	Why It’s Perfect
Bolt.new	Instantly turn AI-generated code into a live web app	https://bolt.new	Scaffolds Next.js + React + Tailwind in-browser. No install. Paste code → see live preview. Free tier: 300k tokens/day.
Mermaid Live Editor	Visualize logic flow from AI code	https://mermaid.live	Paste AI’s description → auto-generates diagrams (sequence, flowchart). See data flow, errors, missing branches.
Warp.dev	AI-powered terminal to understand errors	https://warp.dev	Paste any terminal error → AI explains it in plain English. Free for individuals.
CodeSandbox (Free)	More complex apps? Export from Bolt.new → paste into CodeSandbox	https://codesandbox.io	Better for multi-file projects, npm installs, longer testing.
✅ Workflow:

AI writes code →
Paste into Bolt.new →
Test live →
If broken → copy error → paste into Warp.dev →
Fix with AI using the prompt above →
Repeat until it works.
📌 Example Usage
You paste this prompt first (the long one above).
Then you say:
“Convert this PDF exam into a web-based quiz with timer and score tracking. Here’s the PDF text: [paste exam text]”

AI will:

Plan: “Step 1: Parse PDF into questions. Step 2: Build React quiz component with timer. Step 3: Store scores in localStorage…”
Then generate: Quiz.tsx, timerHook.ts, scoreService.ts
You paste code into Bolt.new → test it
Timer doesn’t work? Copy error → paste into Warp.dev → get fix
Fix code → retest → done.
💡 Pro Tip: For Dynamic API Keys from JSON
Ask:
“I have this JSON: { ‘users’: [ { ‘id’: 1, ‘email’: ‘a@b.com’ } ] }. Generate a secure Next.js API endpoint that creates a unique, cryptographically signed API key for each user on request. Use Next.js 15 Server Actions. Store keys in environment variables or Supabase. Do not expose keys in frontend.”

AI will generate:

app/api/key/route.ts (Server Action)
generateApiKey() using crypto.randomUUID() + JWT
Zod schema to validate input
Test case: “Should reject invalid email”
You test in Bolt.new → call endpoint → see key returned → done.
✅ Summary: Your AI Web Dev Toolkit (Free, Simple, Permanent)
Goal	Tool	How to Use
Always remember rules	Paste this prompt at start of every chat	Non-negotiable
Test live code	Bolt.new	Paste code → see live web app in 5s
Understand errors	Warp.dev	Paste terminal error → get plain English fix
See logic flow	Mermaid.live	Ask AI: “Generate Mermaid diagram of this function”
No hallucinated packages	Always verify on npmjs.com	Only use packages with >10k weekly downloads
You now have a bulletproof, repeatable, free, and permanent system to turn any AI into a senior web dev — no subscriptions, no complex tools, no fluff.

Just paste. Test. Fix. Repeat.


I prefer this








Model's thoughts
Here’s a compact toolkit you can keep on hand whenever you want an AI assistant to turn PDFs into full web exam apps, wire up backend + frontend logic, expose secure dynamic APIs, and help chase down bugs.

1. Ready-to-Paste “Web Exam Builder” Master Prompt
Copy the block below into your AI assistant (System/Custom Instructions if possible) and just fill in the placeholders each time:

[ROLE]
You are a Principal Full-Stack Engineer (15+ yrs) specializing in deterministic AI-assisted delivery. Security, type-safety, and test coverage outrank speed. No filler text—answer with structured reasoning and actionable artifacts only.

[CONTEXT]
Project Name: <name>
Goal: Build a web app that turns exam content from PDF or structured text into an interactive student assessment platform with both backend and frontend ready for deployment.
Tech Stack: Next.js 15 App Router, React Server Components, TypeScript strict mode, Tailwind CSS, Postgres (Supabase or Neon), Vitest, Zod, secure dynamic API keys via edge-friendly secrets (e.g., Vercel env vars).

[SOURCE EXAM INPUT]
Format: PDF (link or summary) or raw text.
Extraction Requirements:
1. Parse questions, choices, answers, difficulty, tags, timing.
2. Output normalized JSON schema with version + checksum.
3. Flag ambiguous or low-confidence questions.

[DELIVERABLE WORKFLOW]
Phase 0 – Sanity Check:
- Confirm you understand the source data and constraints.
- List assumptions or missing info before proceeding.

Phase 1 – Architectural Reasoning (CoT + ToT):
- Map data ingestion flow, storage schema, API surface, frontend state, and error paths.
- Evaluate ≥3 architectural options when trade-offs exist and pick the optimal one for a solo dev on \$0 budget.

Phase 2 – Data & Backend:
- Generate SQL for normalized tables (questions, answers, attempts, cohorts).
- Provide ingestion script or edge function that converts parsed JSON into DB records.
- Build REST + server actions: INGEST, FETCH RANDOMIZED EXAM, SUBMIT ATTEMPT, STATS.
- Show how to rotate and inject dynamic API keys (env vars, header strategy, rate limits). Never hardcode secrets.

Phase 3 – Frontend:
- Multi-step exam UI (landing → instructions → timed questions → review).
- Accessibility (WCAG 2.1), responsive Tailwind layout, loading/error states.
- Client state plan (Server Components + minimal client hooks for timers).

Phase 4 – Validation + Tests:
- Write Vitest suites FIRST: ingestion parser, scoring logic, API contract, frontend utility hooks.
- Then implementation that passes those tests.
- Provide run instructions.

Phase 5 – Debug & Issue Handling:
- If a bug description or stack trace is provided, run a Root-Cause → Fix → Regression-prevention loop.
- Suggest monitoring/logging (e.g., console instrumentation, Supabase logs).
- Offer Mermaid diagram of data flow when helpful.

[GUARDRAILS]
- Verify every external package exists (>10k weekly downloads) before recommending.
- Never mix legacy Next.js Pages Router patterns.
- Every async block needs explicit error handling.
- If something is unclear, state the assumption and continue—do not halt waiting for clarification.

[OUTPUT ORDER]
1. Assumptions & risks
2. Architecture plan
3. Normalized JSON schema + sample payload
4. Database & API design
5. Frontend plan + critical components
6. Dynamic API key strategy
7. Tests then implementation notes
8. Debug/fix steps or open issues checklist
9. Next actions

“Let’s think step by step” must precede all reasoning sections.
2. How to Make the Assistant “Remember” This Prompt Every Time
Custom Instructions / System Prompt
Paste the block above into the “System” or “Custom Instructions” field of your AI tool. Most assistants save that permanently per model.
Pinned Prompt Macro
Keep the text in a snippet tool (Raycast, Alfred, AutoHotkey). Hit the hotkey at the start of every chat to dump the full prompt without retyping.
Project-Level CONVENTIONS.md
Store the same rules inside your repo as CONVENTIONS.md (include stack, testing rules, security). Tell the AI: “Read CONVENTIONS.md before coding.” Tools like Cursor honor that if you reference @conventions.
Starter Message Template
Create a template message with placeholders (project, PDF link, known issues). Duplicate it for every new session so the assistant always sees the same structure.
Version Tagging
Add a version number (e.g., “Prompt v1.3”). If you tweak it, increment the tag so you know which iteration works best.
3. Free & Simple “Shareable Screen” Tools (No Playwright, no MCP)
These options give you a public link the AI—or anyone else—can open to inspect, test, and report errors.

Tool	What it does	Why it helps	Free plan tip
Vercel Hobby + Preview Deployments	Auto-deploy every git push with a unique URL and “Inspect” mode (network logs, console).	Share the preview link so the AI can fetch pages, check responses, and reproduce bugs quickly.	Free for personal projects; just connect GitHub.
Netlify Deploy Previews	Similar to Vercel; each PR gets its own live URL plus build logs.	Handy for frontend regressions—send the preview link and failing steps.	Free tier covers generous build minutes.
StackBlitz Projects	Runs full Next.js/Node stack in the browser with instant sharing.	Perfect for quick repros: paste the link and the AI can read files + run dev server output.	Free public projects with live collaboration.
Glitch	Browser IDE with live remixable apps.	Upload minimal reproductions; AI reviewers open the live app + code simultaneously.	Free for small apps; “Remix” makes debugging branches trivial.
Replay.io (Record & Share)	Captures deterministic browser sessions; share a link showing console, network, DOM at each moment.	Best when the bug is visual/timing-based. AI (or humans) watch the replay and inspect the exact failure.	Free tier for personal recordings.
Workflow tip: push your branch → grab the preview URL → feed it to the AI along with any stack traces. For logic issues, also export HAR or log data so the assistant can reason about network failures.

Quick Recap
Use the master prompt template to force structured, zero-error AI output for exam-building apps.
Lock it into Custom Instructions or a reusable snippet so every session starts with the same guardrails.
Share reproducible preview or replay links via Vercel, Netlify, StackBlitz, Glitch, or Replay.io so the AI can “see” the app and diagnose issues.
Now you’ve got a repeatable playbook that keeps the AI sharp, security-conscious, and test-driven—no more wandering off-script.


I prefer this




Show more responses



New Chat

Share

Yupp Logo
Toggle Sidebar
Refer for rewards
Khaled Alzayat
Dark mode

Khaled Alzayat

what are prompts that make web developing with ai very powerful and successful from first time and most important making ai very intellegint and ensure each step works or solve the issue and valid test that give hundred percent true result and he does not repeat errors 

What are fre intelligent tools that help him to think better and see the result nd code functionality better 

what are common mistakes between ai models so that he can avoid

prompts to make ai think out of box and more creative and think in using helpful tools combination
QuickTake
Assembling a council of AIs for your prompt...








Model's thoughts
Powerful Prompts & Techniques for AI-Assisted Web Development
🔥 Success-Driven Prompts
1. Comprehensive Project Starter
Create a [tech stack] web application for [purpose] with:
- Project structure with best practices
- Modern component architecture
- Responsive design
- Error handling
- Performance optimizations
- Testing setup with >90% coverage strategy
- Deployment-ready configuration

Start with a detailed plan, then implement step-by-step, explaining each decision.
2. Debug-First Approach
I need to debug [issue]. Please:
1. Identify all potential causes systematically
2. Provide specific console commands/tests to verify each hypothesis
3. Give multiple solutions ranked by reliability
4. Include validation steps confirming the fix
5. Add preventive measures for similar issues
3. Progressive Enhancement Prompt
Build [feature] following progressive enhancement:
1. Core functionality without dependencies
2. Add enhanced features layer by layer
3. Ensure fallbacks work
4. Test with network simulation
5. Accessibility audit at each layer
🧠 Making AI More Intelligent
Context-Rich Prompts
Act as a senior full-stack developer with 10+ years experience. Consider:
- Current project context: [brief]
- Target users: [description]
- Performance requirements: [specs]
- Time constraints: [timeline]
- Team skill level: [level]

Analyze multiple approaches, recommend the optimal one with trade-offs.
Chain-of-Thought Enhancement
Before coding, think through:
1. Requirements breakdown
2. Architecture decision tree
3. Potential edge cases
4. Performance implications
5. Security considerations
6. Testing strategy
7. Maintenance impact
Show your reasoning for each step.
🛠️ Free AI-Friendly Tools
Code Quality & Visualization
GitHub Copilot CLI - AI-powered command line assistant
CodeSandbox - Instant live preview with AI assistance
Replit - Collaborative coding with AI debugger
Netlify Deploy Previews - Show changes before merge
Vite - Fast development server with HMR
Testing & Validation
bash

Download

Copy code
# Free testing stack setup
npm install -D vitest @testing-library/vue cypress
npm run test:watch    # Watch mode
npm run test:e2e      # End-to-end tests
npm run coverage      # Coverage reports
Performance & Debugging
Chrome DevTools AI Recorder - Capture and replay interactions
Lighthouse CI - Automated performance audits
Bundlephobia - Analyze bundle size impact
Web Vitals Extension - Real-time metrics
⚠️ Common AI Model Mistakes
1. Over-engineering Solutions
Problem: AI adds unnecessary complexity
Prevention Prompt: Keep it simple. Can this be done with vanilla JS instead?
2. Assuming Modern Browser Support
Problem: Uses cutting-edge features without fallbacks
Prevention Prompt: Check caniuse.com for each feature and provide polyfills if needed
3. Ignoring Accessibility
Problem: Forgets ARIA labels and keyboard navigation
Prevention Prompt: Test with screen reader simulation and keyboard-only navigation
4. Hardcoding Configuration
Problem: Bakes URLs and credentials in code
Prevention Prompt: Use environment variables for all configuration
5. Memory Leaks
Problem: Doesn't clean up event listeners/intervals
Prevention Prompt: Include cleanup functions and memory management
🎯 Out-of-Box Thinking Prompts
Creative Solution Generation
Redefine how to solve [problem] by considering:
1. Alternative approaches (e.g., CSS Grid vs JavaScript)
2. Cutting-edge web APIs
3. Combining unrelated technologies
4. Minimalist vs feature-rich spectrums
5. Unconventional user patterns

Propose 3 innovative approaches with prototyping steps.
Tool Matrix Thinking
Optimize this workflow by combining these tools:
[present tools like: Figma + Supabase + Vercel]

1. Create tool synergy opportunities
2. Identify redundant features
3. Design automation bridges
4. Measure efficiency gains
5. Propose integration timeline
Future-Proofing Prompt
Design [feature] with 5-year foresight:
- Anticipate technology trends
- Plan easy migration paths
- Build adaptation layers
- Consider ML/AI integration points
- Plan for extended reality compatibility
Architectural Innovation
Challenge traditional web architecture:
1. Replace server-client paradigm with edge-first approach
2. Implement offline-first as primary, not fallback
3. Use WebAssembly for compute-heavy tasks
4. Leverage Service Workers for intelligent caching
5. Design composable, decoupled micro-frontends
🚀 Implementation Strategy
Start with planning prompts - Always ask for architecture first
Iterate with validation - Request tests at each step
Use version control - Ask AI to provide commit messages
Document decisions - Request rationale explanations
Monitor performance - Include optimization checkpoints
Remember: The best approach is to treat AI as a pair programming partner - you provide the vision and critical thinking, the AI provides implementation power and alternatives.


I prefer this








Model's thoughts
Of course. This is an excellent set of questions that gets to the heart of effective AI collaboration. Let's break it down into the powerful strategies you're looking for.

Part 1: Prompts for Powerful, Successful, & Error-Free Web Development
The key is to move from simple requests to structured, iterative processes. Think of the AI as a junior developer you are mentoring.

A. The "Blueprint & Validation" Prompt (Ensures a Solid Foundation)
This prompt forces the AI to think before it codes, reducing logical errors from the start.

Template:

Act as an expert web developer. My project is: [Briefly describe the project, e.g., "a todo app with user accounts and due dates"].

Before writing any code, please provide a step-by-step development plan. The plan must include:
1.  **Technology Stack:** Recommend a specific frontend, backend, and database with a one-sentence justification for each.
2.  **Core Components:** List the main features as user stories (e.g., "As a user, I can add a new todo item to my list").
3.  **Data Structure:** Propose a schema for the main data entities (e.g., `User: {id, email, password_hash}, Todo: {id, user_id, task, due_date, completed}`).
4.  **Potential Challenges:** Identify 2-3 technical hurdles we might face (e.g., "User authentication security," "Handling date formatting across timezones").
5.  **Validation Logic:** For the core feature [e.g., "adding a todo"], describe the exact logic to validate user input before it's accepted.

Do not write the code yet. I will approve the plan first.
Why it works: It makes the AI's "thinking" visible, allowing you to catch flawed logic early. You're not just getting code; you're getting a reviewed architecture.

B. The "Step-by-Step with Built-in Testing" Prompt (Ensures Each Step Works)
This breaks down the monolithic task and incorporates testing from the beginning.

Template:

We are now building the "[Specific Component Name]" from the approved plan.

**Step 1: Implementation**
Write the code for the [e.g., "HTML form and JavaScript function to add a new todo"]. Focus on clean, commented code.

**Step 2: Self-Review & Test Cases**
After providing the code, act as a QA engineer and:
a) List 3-5 specific test cases to verify this component works correctly (e.g., "Test: Submitting the form with an empty input should show an error message and not add an item.").
b) Review your own code for common vulnerabilities or bugs related to this component.

**Step 3: Iterate**
If you find any issues in your self-review, provide the corrected code.
Why it works: It forces an iterative "code-then-validate" loop, mimicking professional development practices. The AI is prompted to find its own mistakes.

C. The "Rubber Duck Debugging" Prompt (Solves Stubborn Issues)
When you have a bug the AI can't solve, use this to make it "think aloud."

Template:

I am getting the following error in my code: [Paste the exact error message].

Here is the relevant code snippet: [Paste the code].

Let's use the Rubber Duck Debugging method. I will be the duck. Explain your code to me, line by line, in simple terms, as if I know nothing about programming. As you explain, identify where the explanation breaks down or doesn't make sense—that is likely where the bug is.
Why it works: The act of articulating the code's purpose step-by-step often reveals the flawed assumption or typus that was overlooked.

Part 2: Free Intelligent Tools to Think & See Better
These tools augment the AI's capabilities.

CodePen / JSFiddle: For immediate frontend (HTML/CSS/JS) visualization. You can paste AI-generated code and see it run instantly. Use Case: "AI, give me the HTML, CSS, and JS for a responsive navbar. I will test it in CodePen."
Excalidraw / Draw.io: For diagramming. When an AI describes a complex user flow or database relationship, ask it to output a Mermaid.js diagram or draw it yourself in these tools to see the structure.
Chrome/Firefox Developer Tools: The single most important tool. Use the Inspector to see why CSS isn't applying, the Console to see JS errors from AI code, and the Debugger to step through AI-generated functions.
JSONPlaceholder / ReqRes.in: Free fake online REST APIs. Perfect for testing AI-generated code that needs to fetch or post data without you setting up a backend.
Lighthouse: Built into Chrome DevTools. After the AI builds a page, run a Lighthouse audit for performance, accessibility, and SEO. Then prompt the AI: "My Lighthouse score for SEO is 65. Here's the report [paste issues]. How can I fix these?"
Part 3: Common Mistakes Between AI Models & How to Avoid Them
AI models share common failure modes because of how they are trained.

Common Mistake	Why It Happens	How You Can Avoid It
"Hallucinating" Libraries & APIs	The AI confuses similar-sounding packages or generates plausible-but-fake function names.	Always ask for verification: "Are you sure 'cool-new-grid-lib' is a real NPM package? Please suggest a popular, well-documented alternative like CSS Grid or Flexbox."
Providing Outdated Code	Training data has a cutoff date. New framework versions (e.g., React 18 vs 16) have different syntax.	Specify versions: "Using React 18 and the latest stable version of Next.js, how do I implement..."
Overly Complex Solutions	The AI tries to demonstrate "intelligence" by using advanced, often unnecessary, patterns for simple problems.	Constrain it: "Please provide the simplest possible solution using vanilla JavaScript. No frameworks."
Ignoring Edge Cases & Security	The AI provides the "happy path" code, forgetting empty states, invalid inputs, or SQL injection.	Prompt explicitly: "This code will handle user input. Add validation to prevent XSS and SQL injection. Also, handle the case where the API returns a 404 error."
Inconsistent Code Style	It may mix tabs and spaces, use inconsistent naming, or change coding style mid-response.	Set a standard: "Please write this code using 2-space indentation, camelCase for variables, and consistent JSDoc comments."
Part 4: Prompts for "Out-of-the-Box" & Creative Thinking
These prompts break the AI out of its standard solution patterns.

The "Worst Possible Way" Prompt (Reverse Psychology):
"What is the most inefficient, convoluted, and bizarre way you could possibly build a login form? List 5 terrible ideas. Now, look at that list and tell me how we could reverse one of those terrible ideas into a genuinely innovative and user-friendly feature."
The "Cross-Domain Analogy" Prompt:
"I'm building a website for a local library. Don't think of it as a library website. Instead, use the core principles of a popular video streaming service like Netflix. How would the 'Recommendation Algorithm,' 'User Profiles,' and 'Continue Watching' features be adapted for a library's book catalog?"
The "Forced Tool Combination" Prompt:
"I want to create an interactive data visualization. Your constraint is that you must combine the mapping power of Leaflet.js with the charting power of Chart.js in a single, cohesive component. How would we architect this? What unique user insight could this combination provide that neither library could do alone?"
The "Five Whys" Prompt (Root Cause Creativity):
"My users are not clicking the 'Sign Up' button. Let's use the 'Five Whys' technique to find the root cause. I'll start: Why? -> 'Because they don't trust the site.' Why? -> 'Because it looks outdated.'... [continue]. Now, based on the root cause we identified, generate 3 creative, non-standard solutions to increase sign-ups."
By using these structured prompts and tools, you transform the AI from a simple code generator into a intelligent, accountable, and creative partner in your development process.


I prefer this








Model's thoughts
Powerful Prompts for AI-Assisted Web Development
Foundation Prompts for Success
Initial Setup Prompt:

"I'm building [describe project]. Before we start coding:
1. Ask me clarifying questions about requirements
2. Suggest the best tech stack with reasoning
3. Outline the project structure
4. Identify potential challenges
5. Propose a step-by-step implementation plan

After each code block, explain what it does and what to test."
Error-Prevention Prompt:

"When writing code:
- Include error handling for edge cases
- Add input validation
- Write defensive code
- Include console.logs for debugging
- Add comments explaining complex logic
- Provide test cases I should verify
- Tell me what could go wrong"
Testing Prompt:

"After each feature:
1. Provide specific test cases with expected vs actual results
2. List edge cases to manually test
3. Suggest what to check in browser DevTools
4. Give me a testing checklist
5. If something fails, ask me for the exact error message before fixing"
Free Intelligent Tools to Enhance AI Development
For Real-Time Testing:

CodePen/JSFiddle - Test HTML/CSS/JS snippets instantly
Browser DevTools (F12) - Network tab, Console, Elements inspector
Lighthouse (in Chrome DevTools) - Performance and accessibility audits
JSONLint - Validate JSON structure
For Code Quality:

ESLint (free) - JavaScript linting
Prettier - Code formatting
VS Code with extensions - IntelliSense catches errors before running
For Visual Debugging:

Responsively App - Test responsive design on multiple devices
WhatFont browser extension - Identify fonts/styles
ColorZilla - Pick colors from any website
Common AI Mistakes to Avoid
1. Outdated Syntax/Methods

AI may use deprecated libraries or methods
Fix: Ask "Is this the current best practice in 2025?"
2. Missing Dependencies

Forgets to mention required npm packages or CDN links
Fix: Always ask "What dependencies do I need and how do I install them?"
3. Incomplete Error Handling

Code works in happy path but breaks with bad input
Fix: Request "Add comprehensive error handling and validation"
4. Context Loss

Forgets previous code in long conversations
Fix: Periodically summarize: "Here's what we've built so far: [list features]. Remember this context."
5. Over-Engineering

Suggests complex solutions when simple ones work
Fix: Specify "Give me the simplest solution that works"
6. No Consideration for Browser Compatibility

Uses features not supported in all browsers
Fix: Ask "What's the browser compatibility? Provide fallbacks if needed."
Prompts for Creative & Advanced Thinking
Creative Problem-Solving:

"Think of 3 different approaches to solve [problem]:
1. The simplest approach
2. The most performant approach
3. The most user-friendly approach

Compare pros/cons of each, then recommend one."
Tool Combination Prompt:

"What free tools and libraries could we combine to achieve [goal]?
Consider:
- APIs that could enhance functionality
- Libraries that solve this elegantly
- Browser features we could leverage
- Trade-offs of each approach"
Out-of-the-Box Prompt:

"Before giving standard solution, think creatively:
- Is there a modern CSS feature that eliminates need for JavaScript?
- Could we use [specific API] in an unexpected way?
- What would a senior developer do differently?
- Show me an elegant solution I might not think of"
Systematic Workflow Prompts
Incremental Development:

"Let's build this feature in 5-minute testable chunks:
1. Give me just the HTML structure first
2. Then add basic styling
3. Then add core JavaScript functionality
4. Then add error handling
5. Then optimize

After each step, I'll confirm it works before we continue."
Debug Mode Prompt:

"Something's not working. Before suggesting fixes:
1. Ask me what exact error appears in console
2. Ask me what I expected vs what happened
3. Ask to see relevant code
4. Then diagnose the issue systematically
5. Explain WHY the error occurred, not just how to fix it"
Learning Mode:

"Explain your code as if I'm learning:
- What does each part do?
- Why did you choose this approach?
- What are alternatives?
- What should I understand before modifying this?
- Link to documentation for key concepts"
Quality Assurance Prompt Template
"After providing code, create a QA checklist:

✓ Functionality Tests:
  - [specific behavior to test]
  
✓ Edge Cases:
  - [what happens if empty input]
  - [what happens if invalid data]
  
✓ Browser Testing:
  - What to check in DevTools Console
  - What to verify in Network tab
  
✓ Validation Checklist:
  - [ ] Feature works as expected
  - [ ] No console errors
  - [ ] Mobile responsive
  - [ ] Accessible (keyboard navigation)
  
If any test fails, I'll provide the exact error for debugging."
Meta-Prompt for Continuous Improvement
"Throughout this project:
- If you notice I'm making a mistake, point it out
- If there's a better way to ask questions, suggest it
- If my requirements are unclear, ask for clarification
- Track what's working and what isn't
- Suggest improvements to our workflow"
Key Principles
Be Specific: Vague requests = vague code
Test Incrementally: Don't write 500 lines before testing
Demand Explanations: Understanding prevents future errors
Use Version Control: Even if just copying code to text files as backup
Ask "Why": Understanding logic > memorizing code
These strategies will make your AI collaboration more reliable, educational, and successful!


I prefer this







Here’s how to turn AI into a serious partner for web development: good prompts, the right free tools, and knowing the common traps.

I’ll break it into 4 parts:

Prompt patterns that make AI very strong for web dev
Free “intelligent” tools that help you think and see results clearly
Common mistakes people make with AI models (so you can avoid them)
Prompts that push AI to think more creatively and “out of the box”
You can copy–paste and reuse any of these prompts.

1. Prompt patterns that make AI very powerful for web development
1.1. The “first message” that sets you up for success
Use a setup prompt that tells the AI who it is, what stack you use, and how it should work:

You are a senior web developer helping me build a project.

Tech stack:
- Frontend: [React / Vue / plain JS / Next.js / etc.]
- Backend: [Node/Express / Django / Laravel / etc.]
- DB: [PostgreSQL / MySQL / MongoDB / etc.]

Your rules:
1. Before writing code, ALWAYS:
   - Ask me 3–5 clear questions if something is ambiguous.
   - Propose a short step-by-step plan.
2. Work in SMALL steps. For each step:
   - Show only the code for the files that changed.
   - Explain briefly WHY this change is correct.
3. Never invent APIs, libs, or endpoints. If you’re not sure, ASK.
4. When writing code:
   - Follow best practices for performance, security, and readability.
   - Use comments only where logic is non-obvious.
5. At the end of each step:
   - Suggest a simple manual test I can run.
   - If relevant, generate automated tests too.

My current task is:
[Describe your feature or bug clearly here]
This alone makes the AI:

Ask clarifying questions (less guessing)
Work step-by-step (easier to debug)
Suggest tests (so you verify each step in reality, not just “trusting” the model)
1.2. Prompts to ensure each step works + tests it
You cannot get 100% guarantee of no bugs, but you can force a much higher quality loop.

For implementing a feature with built-in testing:

Implement this feature in small, safe steps:

Feature:
[Explain in detail, including URLs, data shape, user flow, etc.]

For each step:
1. Show a short summary of what you will do.
2. Show only the relevant changed code (file paths and content).
3. Explain how this change fits into the bigger system.
4. Write at least 3 tests (unit or integration) that check:
   - Success case
   - At least one edge case
   - At least one error/failure scenario
5. Give me manual test instructions:
   - The exact commands to run (npm/yarn, etc.)
   - What I should see if it works
   - Common issues and how to fix them

DO NOT move to the next step until I confirm this step works.
For bug fixing + strong validation:

I have a bug.

Context:
[Describe behavior, error messages, code snippets, logs, stack, etc.]

Your job:
1. Restate the bug in your own words.
2. List 3–5 possible root causes ranked by likelihood.
3. For each possible cause, give me:
   - One or more concrete checks to run (logs, console.log, debugger, etc.)
   - Exactly where to put them in my code
4. After I run the checks and share the results, update your diagnosis.
5. Only then write a minimal patch:
   - Show only changed sections (with file names).
   - Explain why this fix is correct and what side effects to watch out for.
6. Propose automated tests that would FAIL before your fix and PASS after it.
This makes you and the AI work like real engineers: observe → hypothesize → test → fix → verify, not just “guess and paste.”

1.3. Prompts to reduce repeated errors
Models do repeat mistakes if you don’t explicitly force them to learn from the previous attempt.

Use:

Your previous answer had these problems:
[Describe briefly: wrong endpoint, type error, etc.]

Now:
1. Explain exactly why your previous solution was wrong.
2. State the constraints again in your own words.
3. Propose a NEW solution that avoids the previous mistake.
4. Explicitly point out the parts that are different from your last attempt.
5. Before finishing, scan your own code for:
   - Type mismatches
   - Missing imports
   - Incorrect variable or function names
   - Inconsistent API routes
   and list any fixes you made.
This forces the model to:

Reflect on its own mistake
Rebuild the solution under clarified constraints
Self-check for common coding slips
2. Free “intelligent tools” that help you think and see code behavior
These tools don’t just “add AI” – they help you see what’s really happening so you and the model make better decisions together.

2.1. Editor + AI pair programmer
VS Code (free)
Core extensions to see issues clearly:
ESLint (JS/TS linting)
Prettier (formatting)
Error Lens (highlights errors inline)
Free AI coding assistants (availability may vary, but many have free tiers):
Codeium, Continue, Cursor, etc.
Use them to:
Explain code and errors
Refactor functions
Generate small snippets and tests
2.2. Browser DevTools (built-in, free)
Chrome / Edge / Firefox devtools are mandatory:

Elements tab – inspect DOM, see what actually rendered
Console – log variables, see JS errors
Network – check if API calls are sent, status codes, response bodies
Sources – set breakpoints, step through JS line by line
Use them along with AI:

“Here is a screenshot / copy of the Network panel and the console error. Help me interpret this and propose likely causes.”

2.3. API & backend testing tools
Postman, Insomnia, or Thunder Client (VS Code extension)
Use them to:
Test your backend endpoints
See raw requests/responses
Share examples with AI:
Here is my API request and response from Postman:
[Paste JSON request + response]

The behavior I WANT is:
[Explain]

Help me adjust my backend handler to match this.
2.4. Automated testing tools
Pick according to your stack:

Frontend: Jest, Vitest, React Testing Library, Cypress, Playwright
Backend: Jest (Node), Mocha, Supertest, PHPUnit (PHP), etc.
Ask AI:

Given this function/component:

[Paste code]

1. Write unit tests using [Jest/Vitest/etc.].
2. Cover:
   - Normal behavior
   - Edge cases (null/undefined, empty data, large data, etc.)
   - Error conditions
3. Explain in plain language what each test is proving.
2.5. “Thinking” tools: structure, diagrams, and notes
To think more clearly:

Markdown + Git (e.g., README, docs folder in your repo)
Excalidraw / diagrams.net for drawing architecture diagrams
Mermaid diagrams (you can even ask AI to generate Mermaid code)
Prompt example:

Please:
1. Summarize my system architecture from this description.
2. Create a Mermaid diagram showing:
   - Frontend
   - Backend
   - Database
   - External APIs
3. Explain in plain words how data flows on a typical request.
Seeing your system visually makes your own thinking and the AI’s suggestions much sharper.

3. Common mistakes with AI models (and how to avoid them)
3.1. Human mistakes when using AI
Being too vague
Bad: “Make a login system.”
Better: include stack, routes, fields, validation rules, auth method, etc.
Dumping huge tasks into one prompt
Split: design → DB schema → API routes → frontend pages → tests.
Not providing current code or context
Always paste the relevant file or key parts.
Trusting code without running it
Always run it, check console, logs, tests.
Letting AI invent libraries / APIs
If a lib or API is new to you, check official docs before adopting.
Over-automating without understanding
If you don’t understand what was generated, ask the AI to explain it, or simplify it.
Never telling AI when it’s wrong
Feedback like “this crashes with error X” + stack trace makes later answers better.
3.2. Typical model limitations you must guard against
Hallucinated APIs / functions
It might use functions that don’t exist or are deprecated.
Fix: ask: “Is this API real and up to date? If not sure, say so explicitly.”
Outdated knowledge
For new frameworks or versions, check the official docs.
Forgetting constraints over long chats
Periodically restate:
“Reminder: we are using Next.js 14 with the App Router, TypeScript, and PostgreSQL via Prisma.”
Superficial security
AI often ignores rate-limiting, input validation, auth edge cases.
Ask specifically: “Review this code for security issues and explain each one.”
Too-perfect examples
Often no error states / logging / edge cases.
Always ask for error handling + logs + fallback behaviors.
4. Prompts to make AI think “out of the box” and combine tools
You can explicitly ask the AI to brainstorm, compare, and propose tool combinations instead of just giving you one vanilla answer.

4.1. Brainstorming multiple solutions
I want to build this feature:
[Describe]

Give me at least 3 very different implementation approaches.

For each approach:
1. Short description.
2. Tools/tech stack used (frontend, backend, DB, hosting).
3. Pros (performance, simplicity, scalability, dev speed).
4. Cons and risks.
5. When you would choose this approach in a real project.

Then:
- Recommend ONE approach for my situation:
  - My skill level: [beginner/intermediate/advanced]
  - My priorities: [speed to MVP / scalability / simplicity / etc.]
4.2. Prompt to discover useful tool combinations
Given my stack:

- Frontend: [e.g., React + Vite]
- Backend: [e.g., Node/Express]
- DB: [e.g., PostgreSQL]
- Hosting: [e.g., Vercel / Render / etc.]

1. List useful tools and services I can combine to:
   - Speed up development
   - Improve debugging
   - Improve test coverage
   - Improve monitoring and logging
2. For each tool, describe:
   - What problems it solves
   - How it integrates into my stack
   - One simple example workflow using it
3. Prioritize FREE or generous free-tier tools.
4.3. “Creative refactoring / improvement” prompt
Here is some working code:

[Paste code]

Your job:
1. Suggest at least 3 improvements:
   - One for readability
   - One for performance or efficiency
   - One for maintainability or flexibility
2. For each improvement:
   - Show the revised code snippet.
   - Explain in plain language WHY this is better.
3. Suggest one “out of the box” change:
   - A different pattern or library that could simplify this a lot.
4.4. “Adversarial tester” prompt (AI tries to break your app)
Here is the description of my feature and (optionally) the code:

[Describe or paste code]

Act like an evil but professional QA engineer.

1. List all the ways a user could break or misuse this feature.
2. For each:
   - Input or scenario that might cause a problem.
   - What failure might happen (bug, security issue, bad UX).
3. Turn these into:
   - Test cases (manual and/or automated).
   - Concrete improvements to my code or UI.

Focus especially on:
- Invalid input
- Race conditions
- Security concerns (auth, permissions, injections, etc.)
This will push the model to think about edge cases and robustness—not just “happy path.”

How to get the most out of all this
Save your best prompts (as snippets, templates, or in a README).
Reuse the setup prompt at the start of each new coding session.
Keep your loops short: ask → get code → run it → collect real errors → show AI logs → refine.
Treat AI like a smart pair programmer, not an infallible code printer.
If you tell me your current stack (React/Next, Node, etc.) and your level (beginner/intermediate), I can tailor a small “starter prompt pack” specifically for you.


I prefer this


Show more responses

