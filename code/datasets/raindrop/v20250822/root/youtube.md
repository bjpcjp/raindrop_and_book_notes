<div class="nav">

⟵ [Up](index.html)  \|  [Index](index.html)

</div>

# youtube

<div class="cards">

<div class="card">

<div class="card-title">

[Funk No.1 - TOKYO GROOVE JYOSHI (feat. Juna Serita & Harumo
Imai)](https://youtu.be/3K8dNctci1Y)

</div>

<div class="card-image">

[![](https://i.ytimg.com/vi/3K8dNctci1Y/hqdefault.jpg)](https://youtu.be/3K8dNctci1Y)

</div>

keyboard vocal Emi Kanazashisax Harumo Imai drums MiMibass Juna
SeritaJuna Serita album : https://linkco.re/gzf64FE3?lang=enInstagram:
https://www.instagram...

</div>

<div class="card">

<div class="card-title">

[How YouTube redrew the TV map - in
graphs](https://digiday.com/marketing/in-graphic-detail-how-youtube-redrew-the-tv-map/?utm_campaign=digidaydis&utm_medium=rss&utm_source=general-rss)

</div>

<div class="card-image">

[![](https://digiday.com/wp-content/uploads/sites/3/2025/02/youtube-revenue-digiday.jpg)](https://digiday.com/marketing/in-graphic-detail-how-youtube-redrew-the-tv-map/?utm_campaign=digidaydis&utm_medium=rss&utm_source=general-rss)

</div>

As YouTube has risen over the past 20 years to the streaming giant it is
today, the platform has changed the way people watch TV.

</div>

<div class="card">

<div class="card-title">

[The hidden world beneath the shadows of YouTube's
algorithm](https://www.bbc.com/future/article/20250306-inside-youtubes-hidden-world-of-forgotten-videos)

</div>

<div class="card-image">

[![](https://ychef.files.bbci.co.uk/624x351/p0kwmcnv.jpg)](https://www.bbc.com/future/article/20250306-inside-youtubes-hidden-world-of-forgotten-videos)

</div>

There's a secret side of YouTube, just beyond the guiding hand of the
algorithm – and it’s nothing like what you know.

</div>

<div class="card">

<div class="card-title">

[YouTube at 20: How the Video Colossus Launched the Creator Economy and
Turned From Hollywood Foe to
Friend](https://variety.com/2025/digital/news/youtube-20th-anniversary-sean-evans-hollywood-1236327520/)

</div>

<div class="card-image">

[![](https://variety.com/wp-content/uploads/2025/03/YouTube-CEO-Neal-Mohan-and-Hot-Ones-host-Sean-Evans-3.jpg?w=1000&h=563&crop=1)](https://variety.com/2025/digital/news/youtube-20th-anniversary-sean-evans-hollywood-1236327520/)

</div>

At 20, YouTube is a multibillion-dollar streamer that powers thousands
of creator businesses and has become a force media companies can't
ignore.

</div>

<div class="card">

<div class="card-title">

[YouTube dominates streaming, forces media companies to
adapt](https://www.cnbc.com/2024/06/26/youtube-streaming-dominance-media-strategy.html)

</div>

<div class="card-image">

[![](https://image.cnbcfm.com/api/v1/image/107432843-17193227042020-03-24t000000z_1592054526_rc2hqf93c9gd_rtrmadp_0_health-coronavirus-youtube.jpeg?v=1719322722&w=1920&h=1080)](https://www.cnbc.com/2024/06/26/youtube-streaming-dominance-media-strategy.html)

</div>

YouTube is gaining share of viewership on TVs, and legacy media doesn't
have a uniform strategy to deal with the threat.

</div>

<div class="card">

<div class="card-title">

[Let's reproduce GPT-2
(124M)](https://m.youtube.com/watch?feature=youtu.be&v=l8pRSuU81PU)

</div>

<div class="card-image">

[![](https://i.ytimg.com/vi/l8pRSuU81PU/maxresdefault.jpg)](https://m.youtube.com/watch?feature=youtu.be&v=l8pRSuU81PU)

</div>

We reproduce the GPT-2 (124M) from scratch. This video covers the whole
process: First we build the GPT-2 network, then we optimize its training
to be really fast, then we set up the training run following the GPT-2
and GPT-3 paper and their hyperparameters, then we hit run, and come
back the next morning to see our results, and enjoy some amusing model
generations. Keep in mind that in some places this video builds on the
knowledge from earlier videos in the Zero to Hero Playlist (see my
channel). You could also see this video as building my nanoGPT repo,
which by the end is about 90% similar. Links: - build-nanogpt GitHub
repo, with all the changes in this video as individual commits:
https://github.com/karpathy/build-nanogpt - nanoGPT repo:
https://github.com/karpathy/nanoGPT - llm.c repo:
https://github.com/karpathy/llm.c - my website: https://karpathy.ai - my
twitter: https://twitter.com/karpathy - our Discord channel:
https://discord.gg/3zy8kqD9Cp Supplementary links: - Attention is All
You Need paper: https://arxiv.org/abs/1706.03762 - OpenAI GPT-3 paper:
https://arxiv.org/abs/2005.14165 - OpenAI GPT-2 paper:
https://d4mucfpksywv.cloudfront.net/better-language-models/language_models_are_unsupervised_multitask_learners.pdf-
The GPU I'm training the model on is from Lambda GPU Cloud, I think the
best and easiest way to spin up an on-demand GPU instance in the cloud
that you can ssh to: https://lambdalabs.com Chapters: 00:00:00 intro:
Let’s reproduce GPT-2 (124M) 00:03:39 exploring the GPT-2 (124M) OpenAI
checkpoint 00:13:47 SECTION 1: implementing the GPT-2 nn.Module 00:28:08
loading the huggingface/GPT-2 parameters 00:31:00 implementing the
forward pass to get logits 00:33:31 sampling init, prefix tokens,
tokenization 00:37:02 sampling loop 00:41:47 sample, auto-detect the
device 00:45:50 let’s train: data batches (B,T) → logits (B,T,C)
00:52:53 cross entropy loss 00:56:42 optimization loop: overfit a single
batch 01:02:00 data loader lite 01:06:14 parameter sharing wte and
lm_head 01:13:47 model initialization: std 0.02, residual init 01:22:18
SECTION 2: Let’s make it fast. GPUs, mixed precision, 1000ms 01:28:14
Tensor Cores, timing the code, TF32 precision, 333ms 01:39:38 float16,
gradient scalers, bfloat16, 300ms 01:48:15 torch.compile, Python
overhead, kernel fusion, 130ms 02:00:18 flash attention, 96ms 02:06:54
nice/ugly numbers. vocab size 50257 → 50304, 93ms 02:14:55 SECTION 3:
hyperpamaters, AdamW, gradient clipping 02:21:06 learning rate
scheduler: warmup + cosine decay 02:26:21 batch size schedule, weight
decay, FusedAdamW, 90ms 02:34:09 gradient accumulation 02:46:52
distributed data parallel (DDP) 03:10:21 datasets used in GPT-2, GPT-3,
FineWeb (EDU) 03:23:10 validation data split, validation loss, sampling
revive 03:28:23 evaluation: HellaSwag, starting the run 03:43:05 SECTION
4: results in the morning! GPT-2, GPT-3 repro 03:56:21 shoutout to
llm.c, equivalent but faster code in raw C/CUDA 03:59:39 summary, phew,
build-nanogpt github repo Corrections: I will post all errata and
followups to the build-nanogpt GitHub repo (link above) SuperThanks: I
experimentally enabled them on my channel yesterday. Totally optional
and only use if rich. All revenue goes to to supporting my work in AI +
Education.

</div>

<div class="card">

<div class="card-title">

[Let's build GPT: from scratch, in code, spelled out. -
YouTube](https://www.youtube.com/watch?v=kCc8FmEb1nY)

</div>

<div class="card-image">

[![](https://i.ytimg.com/vi/kCc8FmEb1nY/maxresdefault.jpg)](https://www.youtube.com/watch?v=kCc8FmEb1nY)

</div>

We build a Generatively Pretrained Transformer (GPT), following the
paper "Attention is All You Need" and OpenAI's GPT-2 / GPT-3. We talk
about connections to ChatGPT, which has taken the world by storm. We
watch GitHub Copilot, itself a GPT, help us write a GPT (meta :D!) . I
recommend people watch the earlier makemore videos to get comfortable
with the autoregressive language modeling framework and basics of
tensors and PyTorch nn, which we take for granted in this video.
Links: - Google colab for the video:
https://colab.research.google.com/drive/1JMLa53HDuA-i7ZBmqV7ZnA3c_fvtXnx-?usp=sharing -
GitHub repo for the video:
https://github.com/karpathy/ng-video-lecture - Playlist of the whole
Zero to Hero series so far:
https://www.youtube.com/watch?v=VMj-3S1tku0&list=PLAqhIrjkxbuWI23v9cThsA9GvCAUhRvKZ -
nanoGPT repo: https://github.com/karpathy/nanoGPT - my website:
https://karpathy.ai - my twitter: https://twitter.com/karpathy - our
Discord channel: https://discord.gg/3zy8kqD9Cp Supplementary links: -
Attention is All You Need paper: https://arxiv.org/abs/1706.03762 -
OpenAI GPT-3 paper: https://arxiv.org/abs/2005.14165 - OpenAI ChatGPT
blog post: https://openai.com/blog/chatgpt/ - The GPU I'm training the
model on is from Lambda GPU Cloud, I think the best and easiest way to
spin up an on-demand GPU instance in the cloud that you can ssh to:
https://lambdalabs.com . If you prefer to work in notebooks, I think the
easiest path today is Google Colab. Suggested exercises: - EX1: The
n-dimensional tensor mastery challenge: Combine the \`Head\` and
\`MultiHeadAttention\` into one class that processes all the heads in
parallel, treating the heads as another batch dimension (answer is in
nanoGPT). - EX2: Train the GPT on your own dataset of choice! What other
data could be fun to blabber on about? (A fun advanced suggestion if you
like: train a GPT to do addition of two numbers, i.e. a+b=c. You may
find it helpful to predict the digits of c in reverse order, as the
typical addition algorithm (that you're hoping it learns) would proceed
right to left too. You may want to modify the data loader to simply
serve random problems and skip the generation of train.bin, val.bin. You
may want to mask out the loss at the input positions of a+b that just
specify the problem using y=-1 in the targets (see CrossEntropyLoss
ignore_index). Does your Transformer learn to add? Once you have this,
swole doge project: build a calculator clone in GPT, for all of +-\*/.
Not an easy problem. You may need Chain of Thought traces.) - EX3: Find
a dataset that is very large, so large that you can't see a gap between
train and val loss. Pretrain the transformer on this data, then
initialize with that model and finetune it on tiny shakespeare with a
smaller number of steps and lower learning rate. Can you obtain a lower
validation loss by the use of pretraining? - EX4: Read some transformer
papers and implement one additional feature or change that people seem
to use. Does it improve the performance of your GPT? Chapters: 00:00:00
intro: ChatGPT, Transformers, nanoGPT, Shakespeare baseline language
modeling, code setup 00:07:52 reading and exploring the data 00:09:28
tokenization, train/val split 00:14:27 data loader: batches of chunks of
data 00:22:11 simplest baseline: bigram language model, loss, generation
00:34:53 training the bigram model 00:38:00 port our code to a script
Building the "self-attention" 00:42:13 version 1: averaging past context
with for loops, the weakest form of aggregation 00:47:11 the trick in
self-attention: matrix multiply as weighted aggregation 00:51:54 version
2: using matrix multiply 00:54:42 version 3: adding softmax 00:58:26
minor code cleanup 01:00:18 positional encoding 01:02:00 THE CRUX OF THE
VIDEO: version 4: self-attention 01:11:38 note 1: attention as
communication 01:12:46 note 2: attention has no notion of space,
operates over sets 01:13:40 note 3: there is no communication across
batch dimension 01:14:14 note 4: encoder blocks vs. decoder blocks
01:15:39 note 5: attention vs. self-attention vs. cross-attention
01:16:56 note 6: "scaled" self-attention. why divide by sqrt(head_size)
Building the Transformer 01:19:11 inserting a single self-attention
block to our network 01:21:59 multi-headed self-attention 01:24:25
feedforward layers of transformer block 01:26:48 residual connections
01:32:51 layernorm (and its relationship to our previous batchnorm)
01:37:49 scaling up the model! creating a few variables. adding dropout
Notes on Transformer 01:42:39 encoder vs. decoder vs. both (?)
Transformers 01:46:22 super quick walkthrough of nanoGPT, batched
multi-headed self-attention 01:48:53 back to ChatGPT, GPT-3, pretraining
vs. finetuning, RLHF 01:54:32 conclusions Corrections: 00:57:00 Oops
"tokens from the \_future\_ cannot communicate", not "past". Sorry! :)
01:20:05 Oops I should be using the head_size for the normalization, not
C

</div>

<div class="card">

<div class="card-title">

[Understanding YouTube Campaign
Types](https://www.practicalecommerce.com/understanding-youtube-campaign-types)

</div>

<div class="card-image">

[![](https://www.practicalecommerce.com/wp-content/uploads/2024/01/Understanding-YouTube-Campaign-Types.jpg)](https://www.practicalecommerce.com/understanding-youtube-campaign-types)

</div>

Google Ads offers seven YouTube campaign subtypes, ranging from reaching
users while browsing to driving conversions.

</div>

<div class="card">

<div class="card-title">

[Adam Sandler: Lunch Lady Land - SNL -
YouTube](https://www.youtube.com/watch?v=VY14zcUM9SI)

</div>

<div class="card-image">

[![](https://i.ytimg.com/vi/VY14zcUM9SI/maxresdefault.jpg)](https://www.youtube.com/watch?v=VY14zcUM9SI)

</div>

Adam Sandler performs "Lunch Lady Land," a song about the lunch lady
(Chris Farley) and how the angry food revolted against her, until Sloppy
Joe (Kevin Nealon) saved the day. \[Season 19, 1994\] \#SNL Subscribe to
SNL: https://goo.gl/tUsXwM Get more SNL:
http://www.nbc.com/saturday-night-live Full Episodes:
http://www.nbc.com/saturday-night-liv... Like SNL:
https://www.facebook.com/snl Follow SNL: https://twitter.com/nbcsnl SNL
Tumblr: http://nbcsnl.tumblr.com/ SNL Instagram:
http://instagram.com/nbcsnl SNL Pinterest:
http://www.pinterest.com/nbcsnl/

</div>

<div class="card">

<div class="card-title">

[What I learned from 100 days of rejection \| Jia Jiang \|
TED](https://youtube.com/watch?si=3jD_ty2RmWhwX0co&v=-vZXgApsPCQ)

</div>

<div class="card-image">

[![](https://i.ytimg.com/vi/-vZXgApsPCQ/maxresdefault.jpg)](https://youtube.com/watch?si=3jD_ty2RmWhwX0co&v=-vZXgApsPCQ)

</div>

Jia Jiang adventures boldly into a territory so many of us fear:
rejection. By seeking out rejection for 100 days -- from asking a
stranger to borrow \$100 to requesting a "burger refill" at a restaurant
-- Jiang desensitized himself to the pain and shame that rejection often
brings and, in the process, discovered that simply asking for what you
want can open up possibilities where you expect to find dead ends.
TEDTalks is a daily video podcast of the best talks and performances
from the TED Conference, where the world's leading thinkers and doers
give the talk of their lives in 18 minutes (or less). Look for talks on
Technology, Entertainment and Design -- plus science, business, global
issues, the arts and much more. Find closed captions and translated
subtitles in many languages at http://www.ted.com/translate Follow TED
news on Twitter: http://www.twitter.com/tednews Like TED on Facebook:
https://www.facebook.com/TED Subscribe to our channel:
http://www.youtube.com/user/TEDtalksDirector

</div>

<div class="card">

<div class="card-title">

[The Secretive, Delightful Man Changing Everything We Know About Theme
Parks](https://slate.com/human-interest/2023/07/disneyland-rides-disney-world-defunctland.html)

</div>

<div class="card-image">

[![](https://compote.slate.com/images/d9f6c4bb-6ad9-40eb-b116-dc286964e6ef.jpeg?crop=1560%2C1040%2Cx0%2Cy0&width=1560)](https://slate.com/human-interest/2023/07/disneyland-rides-disney-world-defunctland.html)

</div>

The only thing more fun than the rides themselves is this guy’s
staggering analysis of them.

</div>

<div class="card">

<div class="card-title">

[From Spotify to YouTube: How I Built a Python Script to Convert
Playlists](https://dev.to/yogeshwaran01/from-spotify-to-youtube-how-i-built-a-python-script-to-convert-playlists-2h89)

</div>

<div class="card-image">

[![](https://media.dev.to/dynamic/image/width=1000,height=500,fit=cover,gravity=auto,format=auto/https%3A%2F%2Fdev-to-uploads.s3.amazonaws.com%2Fuploads%2Farticles%2Fd4d8gecosoughlsh73wd.png)](https://dev.to/yogeshwaran01/from-spotify-to-youtube-how-i-built-a-python-script-to-convert-playlists-2h89)

</div>

I developed the script to convert the Spotify playlist to YouTube
playlist. I am here to share how I...

</div>

<div class="card">

<div class="card-title">

[YouTube Music will let you make your own custom radio
stations](https://www.theverge.com/2023/2/21/23609228/youtube-music-radio-builder-custom-stations)

</div>

<div class="card-image">

[![](https://cdn.vox-cdn.com/thumbor/kSc1MrTy-5jpSGwFwD8Mi2k0Pok=/0x0:2040x1360/1200x628/filters:focal(1020x680:1021x681)/cdn.vox-cdn.com/uploads/chorus_asset/file/23986639/acastro_STK092_03.jpg)](https://www.theverge.com/2023/2/21/23609228/youtube-music-radio-builder-custom-stations)

</div>

You can choose artists, variability, moods, and more.

</div>

<div class="card">

<div class="card-title">

[Why YouTube spent the money on NFL Sunday
Ticket](https://www.theverge.com/2022/12/23/23523280/youtube-nfl-redzone-channel-sunday-ticket)

</div>

<div class="card-image">

[![](https://cdn.vox-cdn.com/thumbor/yiKv0HlcvooA4wEU0howBfyVtgU=/0x0:2040x1530/1200x628/filters:focal(1020x765:1021x766)/cdn.vox-cdn.com/assets/3091121/nfl-logo-stock1_2040.jpg)](https://www.theverge.com/2022/12/23/23523280/youtube-nfl-redzone-channel-sunday-ticket)

</div>

YouTube chief product officer Neal Mohan tells us the steaming giant is
making a big bet on TVs, where it’s seeing the fastest growth.

</div>

<div class="card">

<div class="card-title">

[3 Useful Python Automation
Scripts](https://www.kdnuggets.com/2022/11/3-useful-python-automation-scripts.html)

</div>

<div class="card-image">

[![](https://www.kdnuggets.com/wp-content/uploads/chugh_3_useful_python_automation_scripts_3.jpg)](https://www.kdnuggets.com/2022/11/3-useful-python-automation-scripts.html)

</div>

The post highlights three useful applications of using python to
automate simple desktop tasks. Stay tuned till the end of the post to
find the reference for a bonus resource.

</div>

<div class="card">

<div class="card-title">

[Herbert Hoover vs Fairmont
1977](https://youtube.com/watch?feature=share&v=k8NojS2yQE0)

</div>

<div class="card-image">

[![](https://i.ytimg.com/vi/k8NojS2yQE0/maxresdefault.jpg)](https://youtube.com/watch?feature=share&v=k8NojS2yQE0)

</div>

First round of the AAA WV State Playoffs 1977 (4 teams)

</div>

<div class="card">

<div class="card-title">

[No, YouTube, I will not subscribe to
Premium](https://www.androidauthority.com/youtube-premium-popups-ads-3209067)

</div>

<div class="card-image">

[![](https://www.androidauthority.com/wp-content/uploads/2022/04/YouTube-on-smartphone-stock-photo-18.jpg)](https://www.androidauthority.com/youtube-premium-popups-ads-3209067)

</div>

Do you think YouTube Premium subscription pop-ups and the platform's
burgeoning number of ads are in bad taste? You're not alone.

</div>

<div class="card">

<div class="card-title">

[Download a YouTube video with in 6 lines of
code!](https://twitter.com/driscollis/status/1481297754060173320?s=12)

</div>

🐍🔥 — Mike Driscoll (@driscollis)

</div>

</div>
