---
title: Abstract review
date_received: 2026-05-29
date_due: 2026-06-09
reviewer: Juan
priority: Medium
---

## Read
- [x] Yilin Xie
- [x] Suhas Rao
- [x] Michelle D. Noyes
- [x] Steven J. Losh
- [x] Jennifer A. Karlow
- [x] Rohini K. Gadde
- [x] Trishita Basak

## Score
- [x] Yilin Xie (2)
- [x] Suhas Rao (1)
- [x] Michelle D. Noyes (1)
- [x] Steven J. Losh (1)
- [x] Jennifer A. Karlow (3)
- [x] Rohini K. Gadde (1)
- [x] Trishita Basak (2)

## Notes

*Yilin Xie*: I really like the first abstract that I've read. But I'm a little underwhelmed with regard to the purely predictive nature of the project. That is to say, they're using these sequence Transformer model type predictions to guess at what thematic variants might do in terms of expression. This is a really cool idea, but how will they know if it works?

I must assume that they are basically training on the consortia's data, but what is the likelihood of a given somatic variant arising in multiple donors? This to me would suggest that it is quite unlikely with the number of donors that one could really begin to learn patterns of what a somatic variant might do. Unless of course they're not training based on the consortium's data and they're using some other database, and they're purely trying to predict what it would do. Again, that's interesting, but then how are we meant to use that? I will read more later.

*Suhas Rao*: The second abstract I think is also very interesting, at least interesting to me, in taking the donor specific assembly and goal for essentially enhancing characterization around STRs, meaning short tandem repeats, because these variants are associated with some human diseases. So being able to characterize the repeat length is valuable. I can readily believe that this is a solvable problem, though they don't demonstrate the proof that it's real. That is to say, how do they know that what they are calling as STR expansions are truly that? It is of course just an abstract, so I may be demanding too much. It does seem really incredible that they have found what they believe to be 100-fold expansions of STRs in some tissues. To be honest, that strikes me as generally incredible, as in I'm not entirely sure I believe it without seeing the proof.

*Michelle D. Noyes*: So regarding the third abstract from Michelle, I feel I might have a conflict of interest in that she may end up using my method and in a way we're sort of trying to achieve the same end. But I think she is more so simply trying to use the DSAs to get more accurate calls, whereas I have more or less built an error model based on the DSAs and can basically create a somatic variant at a particular place to demonstrate how it might get mismapped or whether it might get mismapped and where it might move to instead using this framework, my Morgana framework.

But I also fundamentally like this work. It's just that the abstract seems maybe boring, I guess, because I can only choose one of three statuses, one of three scores for each one. And so while I really like the work, I think I might end up giving Michelle a score of two. Like I would definitely enjoy seeing it as a lightning talk, but I also would be okay not seeing it as a lightning talk and instead going to see the poster.

*Steven J. Losh*: Regarding the abstract from Steven Losh, I like it of course. It's basically a tool for improving the detection of somatic mobile element insertions using long read sequencing. He's clearly a part of the mobile element insertions working group, and it is the sort of nitty gritty methods kind of work that I like. But it does feel like the abstracts that I was assigned are perhaps targeted to be maybe a little too much.

I'm also just not 100% sure that I really need to see this particular talk as a lightning talk. I think it's definitely going to be interesting, but I don't know that I believe that it's going to be more interesting than say a talk that focuses on overall the detection of somatic mobile element insertions. So I'm just not 100% convinced given that it's focused on kind of a narrow set of mobile element insertions and a narrow methodology that it's impactful enough for me to really want to see it as a lightning talk. I think it's good, it's definitely at least a two, but I'm not convinced that it deserves a one.

*Jennifer A. Karlow*: I am very interested in the headline method that is being described, which is basically a target capture assay for probing of DNA methylation over transposable elements. It appears to be a short read based assay that uses whole genome bisulfite conversion to probe DNA methylation. But the abstract makes no mention of how this relates to somatic variation.

Of course I can envision that somatic mobile element insertions matter and that repression of such events would matter. But derepression of transposable elements happens with respect to disease, aging, and cancer. I don't believe that the donors that we're working with - that we should anticipate any apparent derepression of transposable elements. And so all this assay would allow us to do is to probe methylation over mobile element insertions, including perhaps some somatic ones. But I have concerns about how we would disambiguate the somatic from the germline.

And given that we are generating long read data from which we can derive DNA methylation estimates, I fail to see the value of this assay to this particular consortium.

*Rohini K. Gadde*: eHAT-seq  on the other hand  is very clearly  fully in line with the goals of this Consortium  I think it clearly needs substantial work to be improved  but this is a great  Direction I think and you know if it works would be highly valuable to the Cinematic mobile elements insertion work  of the Consortium so this one I think definitely deserves a one


*Trishita Basak*: varCUT&Tag is a really cool idea, but I have really significant concerns about the method. I find it very strange that this assay underperforms when using existing variant calling pipelines. As I understand it, these methods are mostly just targeting using epigenetic information and sequence in some sort of way. So other than essentially sampling the genome in a non-standard way, I don't quite understand why existing variant calling tools would underperform using this assay. 

Maybe there's a reason for that, but it doesn't come through in the abstract. So without that information, I must assume that there is just some sort of error or noise or bias that's introduced by the targeting, and that they've adjusted and built their own variant caller to sort of overcome that. But I feel that creates an exceptionally high burden on the authors to prove that these are real events and that they aren't - I'm worried that they are moving the goal posts in order for their variant caller to look good, because I don't understand why existing variant callers would not work with this assay.

So I am inclined to give it a two, even though the utility of such a method I think would be quite high if it really does work.