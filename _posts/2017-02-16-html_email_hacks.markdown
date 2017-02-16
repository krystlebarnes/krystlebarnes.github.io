---
layout: post
title:  "HTML Email Hacks"
date:   2017-02-16 07:52:01 +0000
---


As I mentioned in my previous post, I first taught myself HTML back in the late 90's. In my current role, I somehow picked up the responsibility of preparing all our mass emails in HTML, even though I hadn't worked too much with it since the 90's. Luckily for me, email is still stuck in the 90's, so it didn't take too much effort to refresh my memory and pick up where I left off.

Creating HTML emails comes with a lot of fun issues, mainly due to the variety of email clients that all display HTML a little differently. For the majority of clients, the differences are minor. Then there's Outlook, who is just in it's own Microsoft world. 

One thing Outlook doesn't handle too well is a list. Formatting gets a little funky when using the `<ul>` or `<ol>` tags. Rather than implementing all the different conditional CSS to try to alleviate the formatting issues, I decided to turn all my lists into tables instead. And all was right in the world again.

Here's an example of how I do an unordered list by using a table instead of `<ul>`:

```
<table>
	<tr>
		<td align="left" valign="top" style="padding: 0 0 0 25px;">
			<p style="font-family: Georgia, serif; font-size: 15px; line-height: 26px; color: rgb(90, 90, 90); margin: 0;">
			&bull;
			</p>
		</td>
		<td align="left" valign="top" style="padding: 0 0 0 15px;">
			<p style="font-family: Georgia, serif; font-size: 15px; line-height: 26px; color: rgb(90, 90, 90); margin: 0;">
			Lorem ipsum dolor sit amet, consectetur adipisicing elit. Non repellat ab fugiat accusamus est nostrum deserunt eius nisi unde ullam numquam facere nihil nesciunt explicabo earum sapiente minima, dolorum consequuntur.
			</p>
		</td>
	</tr>
	<tr>
		<td align="left" valign="top" style="padding: 0 0 0 25px;">
			<p style="font-family: Georgia, serif; font-size: 15px; line-height: 26px; color: rgb(90, 90, 90); margin: 0;">
			&bull;
			</p>
		</td>
		<td align="left" valign="top" style="padding: 0 0 0 15px;">
			<p style="font-family: Georgia, serif; font-size: 15px; line-height: 26px; color: rgb(90, 90, 90); margin: 0;">
			Lorem ipsum dolor sit amet, consectetur adipisicing elit. Blanditiis saepe omnis, quia culpa enim, et unde ipsam quam amet iusto debitis. Eius fugit, delectus id vitae, earum quae necessitatibus ut.
			</p>
		</td>
	</tr>
	<tr>
		<td align="left" valign="top" style="padding: 0 0 0 25px;">
			<p style="font-family: Georgia, serif; font-size: 15px; line-height: 26px; color: rgb(90, 90, 90); margin: 0;">
			&bull;
			</p>
		</td>
		<td align="left" valign="top" style="padding: 0 0 0 15px;">
			<p style="font-family: Georgia, serif; font-size: 15px; line-height: 26px; color: rgb(90, 90, 90); margin: 0;">
			Lorem ipsum dolor sit amet, consectetur adipisicing elit. Blanditiis aspernatur repudiandae ab reiciendis praesentium et dolore quas veritatis nam, dolorem a. Voluptatum dolores ipsum ratione hic facilis itaque, a ab.
			</p>
		</td>
	</tr>
</table>
```

<br>

This solution works beautifully across all clients and will look something like this:

<table border="0">
	<tr>
		<td align="left" valign="top" style="padding: 0 0 0 25px;">
			<p style="font-family: Georgia, serif; font-size: 15px; line-height: 26px; color: rgb(90, 90, 90); margin: 0;">
			&bull;
			</p>
		</td>
		<td align="left" valign="top" style="padding: 0 0 0 15px;">
			<p style="font-family: Georgia, serif; font-size: 15px; line-height: 26px; color: rgb(90, 90, 90); margin: 0;">
			Lorem ipsum dolor sit amet, consectetur adipisicing elit. Non repellat ab fugiat accusamus est nostrum deserunt eius nisi unde ullam numquam facere nihil nesciunt explicabo earum sapiente minima, dolorum consequuntur.
			</p>
		</td>
	</tr>
	<tr>
		<td align="left" valign="top" style="padding: 0 0 0 25px;">
			<p style="font-family: Georgia, serif; font-size: 15px; line-height: 26px; color: rgb(90, 90, 90); margin: 0;">
			&bull;
			</p>
		</td>
		<td align="left" valign="top" style="padding: 0 0 0 15px;">
			<p style="font-family: Georgia, serif; font-size: 15px; line-height: 26px; color: rgb(90, 90, 90); margin: 0;">
			Lorem ipsum dolor sit amet, consectetur adipisicing elit. Blanditiis saepe omnis, quia culpa enim, et unde ipsam quam amet iusto debitis. Eius fugit, delectus id vitae, earum quae necessitatibus ut.
			</p>
		</td>
	</tr>
	<tr>
		<td align="left" valign="top" style="padding: 0 0 0 25px;">
			<p style="font-family: Georgia, serif; font-size: 15px; line-height: 26px; color: rgb(90, 90, 90); margin: 0;">
			&bull;
			</p>
		</td>
		<td align="left" valign="top" style="padding: 0 0 0 15px;">
			<p style="font-family: Georgia, serif; font-size: 15px; line-height: 26px; color: rgb(90, 90, 90); margin: 0;">
			Lorem ipsum dolor sit amet, consectetur adipisicing elit. Blanditiis aspernatur repudiandae ab reiciendis praesentium et dolore quas veritatis nam, dolorem a. Voluptatum dolores ipsum ratione hic facilis itaque, a ab.
			</p>
		</td>
	</tr>
</table>
<br>

If you're doing an ordered list, just make sure the width on the `<td>` tag is set and wide enough on different clients (looking at you, Yahoo), or else the characters may end up on a separate line and look something like this:

<table border="0">
	<tr>
		<td align="left" valign="top" style="padding: 0 0 0 25px;">
			<p style="font-family: Georgia, serif; font-size: 15px; line-height: 26px; color: rgb(90, 90, 90); margin: 0;">
			1<br>.
			</p>
		</td>
		<td align="left" valign="top" style="padding: 0 0 0 15px;">
			<p style="font-family: Georgia, serif; font-size: 15px; line-height: 26px; color: rgb(90, 90, 90); margin: 0;">
			Lorem ipsum dolor sit amet, consectetur adipisicing elit. Non repellat ab fugiat accusamus est nostrum deserunt eius nisi unde ullam numquam facere nihil nesciunt explicabo earum sapiente minima, dolorum consequuntur.
			</p>
		</td>
	</tr>
	<tr>
		<td align="left" valign="top" style="padding: 0 0 0 25px;">
			<p style="font-family: Georgia, serif; font-size: 15px; line-height: 26px; color: rgb(90, 90, 90); margin: 0;">
			2<br>.
			</p>
		</td>
		<td align="left" valign="top" style="padding: 0 0 0 15px;">
			<p style="font-family: Georgia, serif; font-size: 15px; line-height: 26px; color: rgb(90, 90, 90); margin: 0;">
			Lorem ipsum dolor sit amet, consectetur adipisicing elit. Blanditiis saepe omnis, quia culpa enim, et unde ipsam quam amet iusto debitis. Eius fugit, delectus id vitae, earum quae necessitatibus ut.
			</p>
		</td>
	</tr>
	<tr>
		<td align="left" valign="top" style="padding: 0 0 0 25px;">
			<p style="font-family: Georgia, serif; font-size: 15px; line-height: 26px; color: rgb(90, 90, 90); margin: 0;">
			3<br>.
			</p>
		</td>
		<td align="left" valign="top" style="padding: 0 0 0 15px;">
			<p style="font-family: Georgia, serif; font-size: 15px; line-height: 26px; color: rgb(90, 90, 90); margin: 0;">
			Lorem ipsum dolor sit amet, consectetur adipisicing elit. Blanditiis aspernatur repudiandae ab reiciendis praesentium et dolore quas veritatis nam, dolorem a. Voluptatum dolores ipsum ratione hic facilis itaque, a ab.
			</p>
		</td>
	</tr>
</table>
<br><br>
For more tips on creating HTML emails, check out some of my favorite email development blogs: [Email on Acid](https://www.emailonacid.com/blog) and [Litmus](https://litmus.com/blog/).
