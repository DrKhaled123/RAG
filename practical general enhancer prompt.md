practical general enhancer prompt.md

Below is a single, self-contained Markdown file that distills the “best-of-both-plans” into a concise, coherent, and action-oriented checklist you can keep open while you code.
Everything is grouped into flexible tips (things you can do right now) and guiding factors (things to keep in mind when you make decisions).
Copy–paste it into code-best-skills.md and you’re done.
markdownDownloadCopy code# code-best-skills.md  
Concise, flexible, non-error-prone tips & factors for writing the best code.

<!-- -------------------------------------------------- -->
## 1. Readability (read > write)
| Tip (do it now) | Guiding factor (keep in head) |
|---|---|
| Rename every variable that needs a comment (`x → taxRate`) | Code is read **10×** more than written |
| Run a formatter (`prettier --write .`) on save | Consistency beats “perfect” style |
| Delete comment that repeats the code; add comment that **explains why** | Comments are debt—pay them down |

<!-- -------------------------------------------------- -->
## 2. Simplicity (KISS & YAGNI)
| Tip | Factor |
|---|---|
| Delete half the code and make it still pass tests | **“If I can’t delete it, I don’t understand it.”** |
| Use language std-lib first; npm second | Every new dep = new attack surface + new bug surface |
| Duplicate once; abstract on the **third** use | Premature abstraction kills flexibility |

<!-- -------------------------------------------------- -->
## 3. Maintainability (change is inevitable)
| Tip | Factor |
|---|---|
| Make every function ≤ 20 lines; if longer → extract | Small things are **easy to swap** |
| Inject dependencies (`processOrder(db, mailer)`) | Hard-coded `new` = hard-to-test |
| Keep pure logic **pure** (no I/O) | Pure fns are **timeless**—cache, test, reuse freely |

<!-- -------------------------------------------------- -->
## 4. Testability (trust through usage)
| Tip | Factor |
|---|---|
| Write the **usage example** first (README or test) | If usage is ugly, API is wrong |
| Mock **at the boundary** (HTTP, DB, file) | Don’t mock your own code |
| Run tests in **watch mode** while you code | Fast feedback loop > perfect test |

<!-- -------------------------------------------------- -->
## 5. Performance (measure → improve)
| Tip | Factor |
|---|---|
| Add `console.time('task')` before any loop | **Profile first, optimise second** |
| Replace `.includes()` inside loops with `Set` | O(n²) → O(n) in one line |
| Stream big files; never `readFileSync` huge data | RAM is **cheaper** than downtime |

<!-- -------------------------------------------------- -->
## 6. Robustness (fail fast, degrade graceful)
| Tip | Factor |
|---|---|
| Validate at public boundaries (`if (!userId) throw...`) | **Never trust** the outside world |
| Return **early** on errors; keep happy path left-aligned | Flat code = readable code |
| Log context (`logger.error('Order failed', {orderId, err})`) | Ops will thank you at 3 a.m. |

<!-- -------------------------------------------------- -->
## 7. Security (assume hostile input)
| Tip | Factor |
|---|---|
| Use **parameterised queries** (`?` placeholders) | SQL-injection is **solved**—just use it |
| Store secrets in env-vars, never in repo | Git history is **forever** |
| Escape output **at render time** (`escapeHtml()`) | XSS is a **rendering** problem, not input problem |

<!-- -------------------------------------------------- -->
## 8. Consistency (team muscle memory)
| Tip | Factor |
|---|---|
| Run `eslint --fix && prettier` on pre-commit | Enforce style **mechanically** |
| Mirror the file tree you see in the project | Principle of **least surprise** |
| Pick one abstraction level per function | Mixed levels = mental jumps |

<!-- -------------------------------------------------- -->
## 9. Documentation (just enough)
| Tip | Factor |
|---|---|
| Write the **README setup** while the steps are fresh | If setup > 3 steps → script it |
| Document **why** the weird code exists, not what it does | Weird without “why” = future bug |
| Keep examples in docstrings executable | Examples **decay**—run them in CI |

<!-- -------------------------------------------------- -->
## 10. Git hygiene (time-travel cleanly)
| Tip | Factor |
|---|---|
| Commit message = `(type): what & why` in 50 chars | `git log --oneline` should tell a story |
| Rebase feature branch before PR → linear history | **Merge bubbles** are noise |
| One logical change per commit (squash WIP) | `git bisect` is your friend |

<!-- -------------------------------------------------- -->
## 11. Learning loop (stay employable)
Daily 30-min cycle:  
1. **Read** 10 min (GitHub trending, blog, RFC)  
2. **Code** 10 min (koan, kata, Advent-of-Code)  
3. **Reflect** 10 min (what did I learn? tweet / note)

Weekly: ship one **tiny** open-source patch (doc fix counts).  
Monthly: delete one old repo and rebuild it with new knowledge.

<!-- -------------------------------------------------- -->
## 12. Pragmatic mindset (ship & sleep)
| Tip | Factor |
|---|---|
| Estimate, then **double** the time | Hofstadter’s law is **real** |
| “Good & shipped” beats “perfect & pending” | Users can’t use code you **didn’t** deploy |
| Know when to **stop** polishing | Polish the **bottleneck**, not the balcony |

<!-- -------------------------------------------------- -->
## 13. Ethical check (people are affected)
Before shipping, ask:  
- Could this be **used to harm** someone?  
- Does it **exclude** people with disabilities?  
- Am I **lying** about what the code can do?

If any answer is “yes”, **change the code or change the requirement**.

<!-- -------------------------------------------------- -->
## Quick start template (copy into new files)
```js
/**
 * <one-sentence what>
 * @param {type} p - description
 * @returns {type} description
 * @example
 * const result = fn(42);
 * console.log(result); // → expectedOutput
 */
export function fn(p) {
  // validation first
  if (typeof p !== 'number') throw new TypeError('p must be number');

  // pure logic
  const out = p * 2;

  // early return
  return out || 0;
}
Run: npm i -D prettier eslint && npx eslint --init → commit → done.
TL;DR cheat-sheet

1. Readability → rename now, format on save
2. Simplicity → delete code, not add
3. Maintainable → inject deps, keep pure
4. Testable → usage first, mock boundary
5. Fast → profile first, Set > loop
6. Robust → validate input, log context
7. Secure → parametrise, env secrets
8. Consistent → auto-lint, mirror project
9. Docs → README setup, why not what
10. Git → story commits, rebase feature
11. Learn → 30-min daily, patch weekly
12. Pragmatic → double estimate, ship early
13. Ethical → harm? exclude? lie? → fix

Keep this file open in a split pane → glance, apply, commit, push.