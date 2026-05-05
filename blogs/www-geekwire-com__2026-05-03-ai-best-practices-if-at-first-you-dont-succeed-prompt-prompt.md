---
title: "AI best practices: If at first you don’t succeed, prompt, prompt again"
url: "https://www.geekwire.com/2026/ai-best-practices-if-at-first-you-dont-succeed-prompt-prompt-again/"
date: "Sun, 03 May 2026 19:37:44 +0000"
author: "Oren Etzioni"
feed_url: "https://www.geekwire.com/feed/"
---
<figure class="wp-block-image size-large"><img alt="" class="wp-image-926697" height="465" src="https://cdn.geekwire.com/wp-content/uploads/2026/05/chatbot-1260x465.jpg" width="1260" /><figcaption class="wp-element-caption">An AI prompt screen, as reimagined by Google Gemini.</figcaption></figure>



<p><em>[Editor&#8217;s Note: This is the third in a series by Oren Etzioni about AI usage and best practices. See also <a href="https://www.geekwire.com/2026/opinion-ai-coach-or-ai-ghostwriter-the-choice-is-yours/">“AI Coach or AI Ghostwriter? The Choice Is Yours,”</a> &nbsp;and <a href="https://www.geekwire.com/2026/opinion-how-to-read-with-ai/">“How to read with AI.”</a>]</em></p>



<p>A friend asked ChatGPT for input on a professional matter and received a banal, lackluster response. I suggested she try a different approach: ask for 15 different ideas, scan them, pick the two that felt most promising, and then ask ChatGPT to refine. She came back overjoyed. ChatGPT had not gotten smarter, but she became better at prompting. </p>



<p>This is my favorite gambit: ask AI for many options, delve deeper into the promising ones, and most importantly, if at first you don’t succeed, prompt, prompt again!</p>



<p>What follows is practical advice on how to use AI as a power tool rather than a slot machine. For a simple request, it’s overkill, but if you’re serious about prompting, read on.</p>



<p>Anthropic’s own guidance for prompting Claude contains a helpful hint: treat the model as a brilliant but literal-minded new employee on their first day. They are capable. They are also new. They will do exactly what you ask, so you have to ask exactly what you want. </p>



<p>The Anthropic team’s golden rule is to show your prompt to a colleague with no context and ask whether they could follow it. If the answer is no, the model can’t either. This principle generates a handful of habits that lift output quality immediately, before any of the more advanced techniques come into play.</p>



<p>One caveat from me, though: don’t think of the model as a person. It’s not. The &#8220;brilliant new employee&#8221; framing is a useful starting point, but it’s a metaphor, not reality. A new hire asks follow-up questions, remembers what you said yesterday, and notices when an instruction is dumb. Claude does none of that by default. Lean on the metaphor to remember to be specific and provide context, but drop it the moment you start to expect human judgment that just isn’t there.</p>



<p>Here’s the playbook, organized as a list for easy reference and periodic review.</p>



<p><strong>Be specific about format, length, audience, and constraints.</strong></p>



<p>Vague prompts produce vague output. The fix is to say what you actually want.</p>



<ul class="wp-block-list">
<li><strong>Before:</strong> Write about marketing trends.</li>



<li><strong>After:</strong> Analyze the three most significant B2B SaaS marketing trends from the past six months. For each, give one company example and a one-sentence assessment of whether the trend will accelerate or plateau. Write it as a 400-word brief for a non-technical board.</li>
</ul>



<p>Improving prompt quality is often simply stating constraints. Vague prompts produce safe, hedged, encyclopedic answers because the model has no signal about what to optimize for and defaults to coverage. Specific prompts produce opinionated, useful answers because the constraints eliminate the safe-but-useless options. Asking for &#8220;three&#8221; instead of &#8220;some&#8221; forces ranking. Asking for &#8220;accelerate or plateau&#8221; forces a call. Asking for &#8220;a board brief&#8221; determines what gets cut. Each constraint you add is a decision the model no longer gets to dodge.</p>



<p><strong>Provide a few examples.</strong></p>



<p>This is the highest-leverage move in everyday prompting. Models pick up patterns from examples faster than from descriptions.</p>



<ul class="wp-block-list">
<li><strong>Before:</strong> Turn these meeting notes into action items.</li>



<li><strong>After:</strong> Turn these meeting notes into action items. Match this format: Example 1: Note: &#8220;Sarah will look into the pricing question and get back to us next week.&#8221; Action item: Sarah → research pricing options → due next Friday. Example 2: Note: &#8220;We agreed to push the launch.&#8221; Action item: Team → revise launch timeline → due before Monday’s standup. Now do the same for these notes: [paste]</li>
</ul>



<p><strong>Tell the model what to do, not what not to do.</strong></p>



<p>Negative instructions are easier to violate than positive ones. Reframing in the affirmative gets you cleaner results.</p>



<ul class="wp-block-list">
<li><strong>Before:</strong> Don’t be too formal. Don’t use jargon. Don’t make it boring.</li>



<li><strong>After:</strong> Write in a warm, conversational tone, the way a smart colleague would explain this over coffee. Use plain English and short sentences.</li>
</ul>



<p><strong>Match the style of your prompt to the style of the output you want.</strong></p>



<p>This one surprises some people. If your prompt is full of bullets and bold text, the model will return bullets and bold text. If you want flowing prose, write in flowing prose.</p>



<p>These habits sound modest. But applied together, they take prompts from the level my friend was operating at, where ChatGPT seemed unhelpful, to a level where AI yields dividends left and right. The advanced techniques in the rest of this piece build on this foundation, but they won’t rescue a prompt that fails the basics.</p>



<p>Beyond the basics, here is a set of effective habits that show up in guidance from OpenAI, Google, working developers, and the people who build production AI systems for a living. These are not techniques so much as workflow disciplines.</p>



<p><strong>Iterate; treat prompting as test-driven.</strong></p>



<p>Your first prompt is a draft. The most experienced practitioners build small sets of test cases (the inputs they care about), run their prompt across them, and refine until the output is consistently good. Several open-source toolkits exist to formalize this loop.</p>



<ul class="wp-block-list">
<li><strong>Before:</strong> Write the prompt. Try it on one example. Looks good. Ship it.</li>



<li><strong>After:</strong> Write the prompt. Pick five inputs, including the awkward edge cases. Run the prompt on all five. Where it fails, change one thing in the prompt and retest. Keep the version that works on the most cases.</li>
</ul>



<p><strong>Specify a definition of done.</strong></p>



<p>OpenAI’s own guidance for GPT-5 stresses telling the model what counts as a finished answer. Without that, the model decides for itself, often by stopping at the first plausible-looking response.</p>



<ul class="wp-block-list">
<li><strong>Before:</strong> Help me debug this Python error.</li>



<li><strong>After:</strong> Help me debug this Python error. You are done when: (1) you have identified the root cause, (2) you have proposed a specific fix with the corrected code, and (3) you have explained why the original failed. If you are not confident on any of those three, say so explicitly rather than guessing.</li>
</ul>



<p><strong>Calibrate effort to the task.</strong></p>



<p>Modern reasoning models have effort or thinking dials. Low effort for extraction and triage; high for synthesis and strategy. Most users leave them on default and pay for it on hard problems.</p>



<ul class="wp-block-list">
<li><strong>Before:</strong> Summarize this 80-page report.&nbsp;</li>



<li><strong>After:</strong> Set thinking effort to high. Read the entire report. Identify the three most important findings, the two weakest claims, and the one question I should ask the authors. Cite page numbers.</li>
</ul>



<p><strong>Inject current or proprietary context directly.</strong></p>



<p>Be careful to avoid jargon and abbreviations unknown to the model (instead of the acronym PMO, say “Project Management Office”). Models don’t have access to your internal documents. Paste in the relevant material.</p>



<ul class="wp-block-list">
<li><strong>Before:</strong> How should I structure a related work section comparing my framework to prior agent governance proposals?</li>



<li><strong>After:</strong> Below is my current draft related work section, plus PDFs of the three papers I am positioning against (pasted). Based only on these sources, identify points of overlap I have not yet acknowledged and any claims in my draft that the cited papers would not actually support.</li>
</ul>



<p><strong>Build a personal prompt library.</strong></p>



<p>This is a power move for a pro. The patterns that worked yesterday are likely to work tomorrow. Stop rewriting them from scratch. Save the prompts that consistently produce good results, organized by task type. Treat them as living documents, not one-off attempts.</p>



<ul class="wp-block-list">
<li><strong>Before:</strong> Open a new chat. Type out the framing, the constraints, the examples, and the question from memory. Watch yourself forget two of them.</li>



<li><strong>After:</strong> Open your prompt library. Copy the &#8220;draft a memo for my manager&#8221; template. Paste in today’s specific topic and source material. Run.</li>
</ul>



<p><strong>Here are some key don’ts</strong>:</p>



<p><strong>Don’t tell reasoning models to &#8220;think step by step.&#8221;</strong></p>



<p>Models like OpenAI’s o-series and GPT-5 thinking already do that internally. Adding the instruction can hurt rather than help. Save it for the everyday models.</p>



<p><strong>Don’t lean on &#8220;do not&#8221; or &#8220;never&#8221; instructions for everything.</strong></p>



<p>Models, especially Gemini, can over-index on broad negative constraints and degrade on basic reasoning. Prefer positive framing: tell the model what to do.</p>



<p><strong>Don’t trust polished prose as evidence of correctness.</strong></p>



<p>Hallucinations are most dangerous when they are well-written. As I pointed out in <a href="https://www.geekwire.com/2026/opinion-how-to-read-with-ai/">How to Read with AI</a>, you have to carefully verify AI output.</p>



<p><strong>Don’t use aggressive language (&#8220;CRITICAL: You MUST…&#8221;).</strong></p>



<p>Modern models are highly responsive to ordinary instructions. Aggressive phrasing can produce overcautious output and triggers refusals. Use normal language.</p>



<p><strong>Don’t include undefined acronyms in your prompt.</strong></p>



<p>They measurably degrade output. For research on the impact of prompt changes see this recent paper on <a href="https://arxiv.org/pdf/2603.13285">Brittlebench</a>.</p>



<p><strong>Don’t change three things at once when iterating.</strong></p>



<p>When a prompt isn’t working, change one variable, test, then change the next. Otherwise you don’t know what helped.</p>



<p><strong>Don’t assume that the same prompt works across models.</strong></p>



<p>Different model families need different prompting. The same instruction can help one and hurt another. The temperature and effort settings that work for GPT are not the ones that work for Claude or Gemini.</p>



<p><strong>Don’t treat the first answer as the final one.</strong></p>



<p>Failing to iterate is a common failure mode in everyday AI use. Here’s a trick for making AI better at multi-step tasks: after each attempt, have the AI write a short critique of what went wrong and tuck that note into its memory for the next try. No fancy mechanics, just the model “talking to itself” in plain English. On the next attempt, it reads its own past reflections and adjusts. This loop can produce meaningful gains over one-shot prompts.</p>



<p>The people who get the most out of AI aren’t the ones with the best prompt templates. They’re the ones who treat the model as a powerful tool for advancing their work. You don’t need to show up with perfect clarity about what you want. A good dialog can get you there, surfacing options and questions you’d have missed on your own. What it can’t do is recognize the right answer when it appears. That part is still on you.</p>



<p><strong>For further reading</strong> &#8230;</p>



<p><strong>Provider documentation</strong>:</p>



<ul class="wp-block-list">
<li>Anthropic prompt engineering <a href="https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/claude-4-best-practices">best practices</a>.</li>



<li>OpenAI prompt <a href="https://platform.openai.com/docs/guides/prompt-engineering">engineering guide</a>.</li>



<li>OpenAI GPT-5 <a href="https://developers.openai.com/api/docs/guides/prompt-guidance">prompt guidance</a>.</li>



<li>Google Gemini <a href="https://ai.google.dev/gemini-api/docs/prompting-strategies">prompting strategies</a>.</li>



<li>Google Vertex AI <a href="https://cloud.google.com/vertex-ai/generative-ai/docs/learn/prompts/prompt-design-strategies">prompt design</a>.</li>
</ul>



<p><strong>Practitioner resources</strong>:</p>



<ul class="wp-block-list">
<li><a href="https://www.promptfoo.dev/docs/intro/">Promptfoo</a> (test-driven prompt engineering).</li>



<li><a href="https://github.com/preset-io/promptimize">Promptimize</a> (Preset, test-driven prompts).</li>



<li><a href="https://www.prompthub.us/blog/everything-you-need-to-do-before-prompting-success-criteria-test-cases-evals">PromptHub</a> (success criteria and evals).</li>



<li><a href="https://github.com/resources/articles/what-is-prompt-engineering">GitHub</a> on prompt engineering practice.</li>
</ul>



<p><em>Editor’s note: GeekWire publishes guest opinions to foster informed discussion and highlight a diversity of perspectives on issues shaping the tech and startup community. If you’re interested in submitting a guest column, email us at&nbsp;<a href="mailto:tips@geekwire.com">tips@geekwire.com</a>. Submissions are reviewed by our editorial team for relevance and editorial standards.</em></p>
