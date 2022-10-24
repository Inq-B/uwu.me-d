# uwu.me-d

# Start

We load up the site, open dev console. Checking the “Network” tab after a refresh we see several files. In these files, there is a loader.js file 	that is somewhat obfuscated.

# Further Analysis

Upon further inspection, the initial line is unescaped and converted to hex bytes. We can use a console.log to see what it’s doing.

```js
<script language="javascript">
function dF(s){
	var s1=unescape(s.substr(0,s.length-1)); 
    var t='';
	for(i=0;i<s1.length;i++){
        t+=String.fromCharCode(s1.charCodeAt(i)-s.substr(s.length-1,1));
    };
    document.write(unescape(t));
}
</script>
```

This exposes a function that takes a variable labelled "s". This variable is again unescaped and converts any hexbytes within to their normal form. It also takes several substrings from the "s" variable. 

# Final

The final string is a listener that executes once the page is loaded. In this function, we can see a large string get passed to our previously deobfuscated "dF" function. 

```js
document.addEventListener('DOMContentLoaded', function() {
       dF('*8H*76ITHY%5EUJ*75myrq*8J*5F*8Hmyrq*8J*5F*75*75*75*75*8Hmjfi*8J*5F*75*75*75*75*75*75*75*75*8Hrjyf*75uwtujwy%7E*8I*77ynyqj*77*75htsyjsy*8I*77z%7Cz3rj*77*8J*5F*75*75*75*75*75*75*75*75*8Hrjyf*75uwtujwy%7E*8I*77ijxhwnuynts*77*75htsyjsy*8I*77z%7Cz3rj*77*8J*5F*75*75*75*75*75*75*75*75*8Hrjyf*75uwtujwy%7E*8I*77zwq*77*75htsyjsy*8I*77myyux*8F44z%7Cz3rj*77*8J*5F*5F*75*75*75*75*75*75*75*75*8Hrjyf*75uwtujwy%7E*8I*77tl*8Fynyqj*77*75htsyjsy*8I*77z%7Cz3rj*77*8J*5F*75*75*75*75*75*75*75*75*8Hrjyf*75uwtujwy%7E*8I*77tl*8Fxnyjdsfrj*77*75htsyjsy*8I*77z%7Cz3rj*77*8J*5F*75*75*75*75*75*75*75*75*8Hrjyf*75uwtujwy%7E*8I*77tl*8Fijxhwnuynts*77*75htsyjsy*8I*77z%7Cz3rj*77*8J*5F*75*75*75*75*75*75*75*75*8Hrjyf*75uwtujwy%7E*8I*77tl*8Fnrflj*77*75htsyjsy*8I*77myyux*8F44z%7Cz3rj4fxxjyx4rjinf4ixdnhts3usl*77*8J*5F*5F*75*75*75*75*75*75*75*75*8Hynyqj*8Jz%7Cz3rj*8H4ynyqj*8J*5F*75*75*75*75*75*75*75*75*8Hqnsp*75wjq*8I*77nhts*77*75y%7Euj*8I*77nrflj4%7D2nhts*77*75mwjk*8I*77fxxjyx4rjinf4kf%7Bnhts3nht*77*8J*5F*5F*75*75*75*75*75*75*75*75*8Hqnsp*75wjq*8I*77xy%7Eqjxmjjy*77*75mwjk*8I*77fxxjyx4hxx4xy%7Eqjx3hxx*77*75y%7Euj*8I*7%3Cyj%7Dy4hxx*7%3C*8J*5F*75*75*75*75*75*75*75*75*8Hqnsp*75wjq*8I*77xy%7Eqjxmjjy*77*75mwjk*8I*77myyux*8F44hisox3hqtzikqfwj3htr4fof%7D4qngx4ktsy2f%7Cjxtrj4%3B36374hxx4fqq3rns3hxx*77*75y%7Euj*8I*7%3Cyj%7Dy4hxx*7%3C*8J*5F*75*75*75*75*75*75*75*75*8Hqnsp*75wjq*8I*77uwjhtssjhy*77*75mwjk*8I*77myyux*8F44ktsyx3lttlqjfunx3htr*77*8J*5F*75*75*75*75*75*75*75*75*8Hqnsp*75wjq*8I*77uwjhtssjhy*77*75mwjk*8I*77myyux*8F44ktsyx3lxyfynh3htr*77*75hwtxxtwnlns*8J*5F*75*75*75*75*75*75*75*75*8Hqnsp*75mwjk*8I*77myyux*8F44ktsyx3lttlqjfunx3htr4hxx7*8Kkfrnq%7E*8IPfwqf*7%3Binxuqf%7E*8Ix%7Cfu*77*75wjq*8I*77xy%7Eqjxmjjy*77*8J*5F*75*75*75*75*8H4mjfi*8J*5F*75*75*75*75*8Hgti%7E*8J*5F*75*75*75*75*75*75*75*75*8H%7Bnijt*75ni*8I*77gfhplwtzsid%7Bnijt*77*75uqf%7Exnsqnsj*75qttu*75rzyji*8J*8H4%7Bnijt*8J*5F*75*75*75*75*75*75*75*75*8Hin%7B*75ni*8I*77%7Bnijtdht%7Bjw*77*8J*8H4in%7B*8J*5F*75*75*75*75*75*75*75*75*8Hin%7B*75ni*8I*77t%7Bjwqf%7E*77*8J*8H4in%7B*8J*5F*5F*75*75*75*75*75*75*75*75*8Hin%7B*75hqfxx*8I*77%7Bnj%7Cutwy*77*8J*5F*75*75*75*75*75*75*75*75*75*75*75*75*8Hu*75ni*8I*77ynrjxyfru*77*8J55*8F55*8F55*8H4u*8J*5F*75*75*75*75*75*75*75*75*75*75*75*75*8Hu*75hqfxx*8I*77yj%7Dy*77*8Jz%7Cz3rj*8H4u*8J*5F*75*75*75*75*75*75*75*75*75*75*75*75*8Hin%7B*75hqfxx*8I*77gzyytsx*77*8J*5F*75*75*75*75*75*75*75*75*75*75*75*75*75*75*75*75*8Hn*75hqfxx*8I*77kf2xtqni*75kf2uqf%7E*75m%7Bw2lwt%7C*77*75tshqnhp*8I*77ytllqjdrzyj*7%3D*7%3E*77*8J*8H4n*8J*5F*75*75*75*75*75*75*75*75*75*75*75*75*75*75*75*75*8Hf*75mwjk*8I*77myyux*8F44lny3z%7Cz3rj4*77*75yfwljy*8I*77dgqfsp*77*8J*8Hn*75hqfxx*8I*77kf2gwfsix*75kf2lnyqfg*75m%7Bw2lwt%7C*77*8J*8H4n*8J*8H4f*8J*5F*75*75*75*75*75*75*75*75*75*75*75*75*8H4in%7B*8J*5F*5F*75*75*75*75*75*75*75*75*75*75*75*75*8Hin%7B*75ni*8I*77kttyjw*77*8J*5F*75*75*75*75*75*75*75*75*75*75*75*75*75*75*75*75*8Hu*75hqfxx*8I*77xrfqqdyj%7Dy*77*8J*5F*75*75*75*75*75*75*75*75*75*75*75*75*75*75*75*75*75*75*75*75nsvznwnjx*752*75*8Hf*75mwjk*75*8I*75*77rfnqyt*8FnEz%7Cz3rj*77*8JnEz%7Cz3rj*8H4f*8J*5F*75*75*75*75*75*75*75*75*75*75*75*75*75*75*75*75*8H4u*8J*5F*75*75*75*75*75*75*75*75*75*75*75*75*8H4in%7B*8J*5F*75*75*75*75*75*75*75*75*8H4in%7B*8J*5F*5F*75*75*75*75*75*75*75*75*8H*7622*75myyux*8F44lnymzg3htr4wnxmfgmu4gnijt3ox*7522*8J*5F*75*75*75*75*75*75*75*75*8Hxhwnuy*75xwh*8I*77fxxjyx4ox4gnijt3ox*77*8J*8H4xhwnuy*8J*5F*75*75*75*75*75*75*75*75*8Hxhwnuy*75xwh*8I*77fxxjyx4ox4rfns3ox*77*8J*8H4xhwnuy*8J*5F*75*75*75*75*75*75*75*75*8Hxhwnuy*75xwh*8I*77fxxjyx4ox4wjxtzwhjx3ox*77*8J*8H4xhwnuy*8J*5F*75*75*75*75*8H4gti%7E*8J*5F*8H4myrq*8J5');
});
```

The way this function is obfuscated is a little different to the previous function. Where the previous function was only unescaped, this one is wrapped in several layers. Firstly, there's the initial unescape caused by this line.

```js 
var s1=unescape(s.substr(0,s.length-1)); 
var t = "";
```

The variable "t" is then declared and appended to in the for... loop declared within dF
```js
	for(i=0;i<s1.length;i++){
        t+=String.fromCharCode(s1.charCodeAt(i)-s.substr(s.length-1,1));
    };
```
This line iterates through the string and gets the character code at the value. The interesting part is that this character code is shifted up by 5.
The cipher is undone by using the s.length substring, which equals to 5.
