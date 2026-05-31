So picture this. You're walking around your neighborhood, phone in your pocket, and you're talking to an AI assistant. Not typing. Talking. You're dictating problems you want it to chew on later — research papers to read, models to train, code to write. Each one comes out as a little structured document, and later you sit down at your laptop and tell the assistant to go solve them. One by one.

That's the actual workflow. And the project we were sitting inside, called tg-problem-statements, exists because of one annoying gap. The assistant's own app doesn't really do voice on every session yet. So Telegram has become the dependable middleman — voice in through Telegram, structured problem statement out, and then a manual hand-off to the right session on the laptop.

Now, on the list of problems Vivek was planning to feed this assistant, one entry stood out. It was kind of meta. It said: figure out how to make Telegram talk to many of these assistant sessions at the same time. Because if you could pull that off — if you could fan one voice channel out to many AI sessions in parallel — then this whole project goes away. You wouldn't need the middleman anymore. You'd just talk straight to each session.

So this one entry was, in a real sense, the self-destruct button for the whole repository. The problem whose solution would put the project out of business. Pretty fun premise.

We went looking. Dispatched a little swarm of research agents. One read the official Telegram plugin docs. One went and inspected the actual source code on GitHub. One combed through blogs and community projects to see if anyone had already pulled this off.

The picture that came back was mixed. The official plugin does technically let you run multiple sessions — but each one needs its own bot, its own private state folder, and there's a quiet trap waiting. Every instance of the assistant tool that's running on your laptop, even the editor extensions you forgot were installed, will silently start its own listener. They end up fighting over messages. Some get delivered to one session, some get delivered to another, and some just get silently dropped. There's an open bug report on it.

The community had built workarounds. There are these relay projects — one called shaike1/relay is the popular one — and they take a totally different approach. Instead of being polite citizens that speak the official protocol, they pretend to be a human typing into a terminal pane. Clever hack. But it would break every custom rule Vivek had built up around the official message format. The voice transcription pipeline. The food-photo detector. The WhatsApp generalization. All of those listen for a very specific message shape, and the community relay just doesn't produce that shape.

So we had a real tradeoff sitting on the table. Pay an ongoing tax — careful configuration with the official multi-bot setup, hoping no editor extension wakes up and steals a message. Or pay a one-time tax — migrate to the community relay and rewrite all the custom rules.

And we were about to weigh those, seriously, when Vivek pulled the whole conversation up to a higher altitude.

He said: wait, what about Amdahl's Law?

Now if you haven't seen this one before — Amdahl's Law is an old argument from the world of parallel computing. A guy named Gene Amdahl wrote it down in 1967, and it's basically a buzzkill. It says: every workload you might want to speed up has parts that are inherently serial. Parts you can't break up across multiple machines no matter how many you have. And as you keep adding processors, that serial part ends up dominating the whole time. Parallel computing is not a free lunch. It has hard ceilings, baked into the structure of the problem.

When you point that lens at Vivek's workflow, the realization is a little uncomfortable but it's clean. The bottleneck here is not the Telegram bot. It's not the listener architecture. It's not anything Anthropic might ship in some future release. It's him. One brain. One mouth. One stream of attention. Dictating a problem happens at the speed of speech, through one person, one statement at a time. No infrastructure on Earth can remove that.

And the moment you see that, the original question starts to dissolve.

Because the workflow actually has two phases, and they have completely different shapes. Phase one is setup. Listing the problems. Sorting them into the easy ones and the gnarly ones. Dictating each one out loud. That phase is unavoidably serial. It's serial because Vivek is doing it. Phase two is execution. Once a problem is well-formed, the assistant runs autonomously on it. That phase is genuinely parallel — you can have ten sessions all working at the same time — and importantly, that phase needs no voice at all. The agent is just working.

Once you see that split, watch what happens to the multi-channel question.

In the setup phase, more Telegram channels do nothing for you. Because you can only voice-talk to one channel at a time anyway. The other nine would just sit there, idle, waiting their turn. In the execution phase, voice isn't needed at all. So extra channels are irrelevant.

The whole original problem statement turned out to be what you'd call a category error. It was a fix for a problem that doesn't structurally exist. There's nothing to fan out from. The serial piece isn't in the wire. It's in the human.

Here's where it gets really fun. We did a thought experiment. Imagine an ideal world where the assistant ships first-class voice support on every session and has some beautiful cross-session view on the phone. Total dream setup. Then compare that ideal world side-by-side with what Vivek has today.

The setup phase looks the same in both. One voice, one brain. The execution phase looks the same in both. Autonomous, no voice. Almost every step lines up perfectly.

The only difference — the only structural difference — is that in today's setup, after Vivek finishes dictating a problem, he has to copy that one file from this project's folder into the target project's folder before launching the agent. One file copy per problem.

That's it. That's the entire gap between this project and the imagined utopia. One file copy.

So the whole conclusion flips. This project is not a temporary workaround waiting to be obsoleted by some future Anthropic release. Under the constraint that there's one human at the helm — and there always will be one human at the helm — this is the right architecture. It's Amdahl-optimal. The only knob worth turning isn't a technical one.

It's discipline. Stay within one topic area per session.

Because here's what was actually painful in that day's session. It wasn't the Telegram setup. It wasn't bot tokens or state folders. It was the cognitive cost of jumping from research-paper problems to model-training problems and back again. Same-domain dictation flows. Cross-domain dictation stalls. The brain doesn't context-switch for free.

So the lesson from the whole excursion is short. Don't build more Telegram channels. Don't adopt the community relays. Don't wait for Anthropic to ship anything fancy. Keep doing this — one domain at a time. And copy the file when you're done.

That's the whole shape of it. A self-destruct button that, when you looked at it carefully, turned out not to be a button at all. Just a reminder that the bottleneck has always been the one place you can't put more hardware. Between the ears.
