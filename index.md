# My meme!

## My motivation
I created this meme because I think it is quite relevant to the world as we know it today. The world:
1. is full of problems
2. has a bigger social divide than at any time during the last half century
3. has politicians that are increasingly oblivious to the needs of their constituents
4. is full of lies, disinformation and propoganda
5. is ruled by profit and re-election priorities, rather than with a focus on improving the lives of the Earth's inhabitants.

This meme represents the frustrations a lot of people have. From my conversations with people, nobody goes to a protest unless they are desperate for change, yet the protestors are not only being ignored but *they are being scorned, mislabelled, and physically dispersed*. This has happened in [Canada](https://fortune.com/2022/02/21/canada-ottawa-freedom-convoy-protest-ends-truckers-arrest-covid-vaccine-mandate/) and now **even here** in our beautiful country of [New Zealand](https://www.aljazeera.com/news/2022/2/10/move-on-new-zealand-police-break-up-wellington-trucker-protest). 

Whatever your views on any recent social problem, protesting is a human right in free countries and we must all be aware that our freedoms are being taken from us day by day and hour by hour. As the famous economist Milton Friedman once said:

> "_There is nothing more permanent than a temoporary government program._" - Milton Friedman, American Economist and Nobel Laureate


Please think about the life you're living now and whether this is the life you want your children and their children to live. Thank you.

### Milton Friedman
<p align="center">
  <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/2/20/Portrait_of_Milton_Friedman.jpg/800px-Portrait_of_Milton_Friedman.jpg" width=500 />
</p>


## How the meme is original
To be honest, I am not about any meme styles. When creating this meme, I had an idea in my head for how I wanted it to come out and that's what I made.

## The meme itself:
<p align="center">
  <img src=my_meme.png width=500 />
</p>


## The code used for creating my meme:
```{r setup, include = FALSE}
install.packages("magick")
library(magick)

#creating the text I will use in the meme
my_text <- c("You have the right to protest...", "...but nobody said there\nwill be results.")

#defining the size (width) of the meme
my_size <- 1000

#Getting images from the web, cropping, scaling + extras for creativity
presidents <- image_read("https://github.com/ClassicMMT/Stats220/blob/main/newzealandexempt.jpg?raw=true") %>%
  image_crop("1967x1000+0+125") %>%
  image_scale(my_size)

new_zealand <- image_read("https://gdb.voanews.com/AE0DD2BB-831D-4B6F-9F0D-5C1B4B2284E4_w1023_r1_s.jpg") %>%
  image_crop("575x575+350") %>%
  image_scale(my_size / 2) %>%
  image_blur(1,1) #just making it look more like the presidents image.

canada <- image_read("https://www.ft.com/__origami/service/image/v2/images/raw/https%3A%2F%2Fd1e00ek4ebabms.cloudfront.net%2Fproduction%2F2e807d3e-eccc-4762-add1-de6bfb460c2c.jpg?fit=scale-down&source=next&width=700") %>%
  image_crop("394x394+150") %>%
  image_scale(my_size / 2) %>%
  image_blur(1,1)

united_states <- image_read("https://content.fortune.com/wp-content/uploads/2021/01/State-Trump-Protests-2021-01-06T201807Z_1550641537_MT1USATODAY15402712_RTRMADP_3_JAN-6-2021-SPRINGFIELD-IL-USA-TONYA-POWERS-LEFT-ALONG.jpg?resize=1500,1000") %>%
  image_crop("1000x1000+250") %>%
  image_scale(my_size / 2) %>%
  image_blur(1,1)

australia <- image_read("https://images.theconversation.com/files/433057/original/file-20211122-17-1y8mb83.jpg?ixlib=rb-1.1.0&q=45&auto=format&w=1200&h=1200.0&fit=crop") %>%
  image_scale(my_size / 2) %>%
  image_blur(1,1)


#Creating blank black rectangles with annotations from my_text
black_box <- image_blank(color = "black", width = my_size, height = 100) %>%
  image_annotate(text = my_text[1], 
                 size = 60, 
                 font = "Impact", 
                 gravity = "center", 
                 color = "white")
black_box2 <- image_blank(color = "black", width = my_size, height = 150) %>%
  image_annotate(text = my_text[2], 
                 size = 60, 
                 font = "Impact", 
                 gravity = "center", 
                 color = "white")

#creating row vectors to later append together
row1_vector <- c(presidents, black_box)
row2_vector <- c(united_states, new_zealand)
row3_vector <- c(australia, canada)

#creating the actual rows
row1 <- image_append(row1_vector, stack = T)
row2 <- image_append(row2_vector)
row3 <- image_append(row3_vector)

#putting the meme together
meme_vector <- c(row1, row2, row3, black_box2)
meme <- image_append(meme_vector, stack = T)

#saving the meme
image_write(meme, path = "my_meme.png", format = "png")

```
