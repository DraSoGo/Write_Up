```bash
nc fickle-tempest.picoctf.net 56640
Encrypted message:
Ne iy nytkwpsznyg nth it mtsztcy vjzprj zfzjy rkhpibj nrkitt ltc tnnygy ysee itd tte cxjltk

Ifrosr tnj noawde uk siyyzre, yse Bnretèwp Cousex mls hjpn xjtnbjytki xatd eisjd

Iz bls lfwskqj azycihzeej yz Brftsk ip Volpnèxj ls oy hay tcimnyarqj dkxnrogpd os 1553 my Mnzvgs Mazytszf Merqlsu ny hox moup Wa inqrg ipl. Ynr. Gotgat Gltzndtg Gplrfdo 

Ltc tnj tmvqpmkseaznzn uk ehox nivmpr g ylbrj ts ltcmki my yqtdosr tnj wocjc hgqq ol fy oxitngwj arusahje fuw ln guaaxjytrd catizm tzxbkw zf vqlckx hizm ceyupcz yz tnj fpvjc hgqqpohzCZK{m311a50_0x_a1rn3x3_h1ah3xim3eKhQa}

Zmp fowdt cjwl-jtnusjytki oeyhcivytot tq a vtwygqahggptoh nivmpr nthebjc, wgx xajj lruzyd 1467 hd Weus Mazytszf Llhjcto.

Yse Bnretèwp Cousex nd tnjceltce ytxeznxey hllrjo tnj Llhjcto Itsi tc Argprzn Nivmpr.

Os 1508, Uonfynkx Eroysesnfs osgetypd zmp su-hllrjo tggflg wpczf (l mgycid tq snnqtki llvmlbkyd) tnfe wuzwd rfeex gp a iwttohll itxpuspnz tq tnj Gimjyèrk Htpnjc.

Bkqwayt’d skhznj gzoqqpt guaegwpd os 1555 ls g hznznyugytot tq tnj qixxe. Tnj wocjc hgqgey tq tnj llvmlbkyd axj yoc xsilypd xjrurfcle, gft zmp arusahjes gso tnj tnjji lkyeexx lrk rtxki my sjlny tq a sspmustc qjj pnwlsk, bsiim nat gp dokqexjyt cneh kfnh itcrkxaotipnz.
```

identify เหมือนเดิมว่ามันคืออะไร

![[Pasted image 20260710144226.png]]

น่าจะเป็น Vigenere Cipher

bruteforce

![[Pasted image 20260710144303.png]]

KEY = FLAG

```txt
It is interesting how in history people often receive credit for things they did not create  
  
During the course of history, the Vigenzlp Wjjsys blm cyph sythwyynfx xuos ecnyd  
  
Cu qlm guwmffj uuncccoeye nz Vmutmf xp Pjaphzmj fn dy bvn twdbnsvgqd yzxhmdgjy ds 1553 gt Bntqvs Gvoynnof Gzgqfnj ns cdx gjjp Qv xnkmv ijg. Nnl. Bdtavi Gfoonxov Gjggfxj  
  
Atw ocj nhkqjhzsyvonti jk ycdx hdkmjm v yfwgj nn atwhzi gt nqnydsl ocj qjrjw cvqk ja fs jminivwd vgumvwjy ajw fi vuuvmjsogd wviith izrwzw ta kqfxzx bdom wznujxo yt ocj zkkjw cvqkkdhtXOK{g311v50_0m_a1li3m3_h1uc3mig3zZhKv}  
  
Omj adwxo rjqg-ythphjsozi iznhwdkynji tk v ktqtvqucvgjodh hdkmjm ctbzqjw, rvx rvyj fmjzsy 1467 wd Qzjs Gvoynnof Fgwjwod.  
  
Ymz Qnlzieqk Roontx hy indxtlnxt ynstzhsty bgardj ind Gahdxio Cohi nx Prakgzh Ixvgkg.  
  
Om 1508, Pdnztckr Zgosntshah ombttsks zgk hu-bgardj igaaag qkrzz (g bgsxxd nl hnhlikc gavggqksy) inzz lutrs rzztx ak p iqoiobga inseumkcz nl ind Bxmdttre Cipher.  
  
Bellaso’s second booklet appeared in 1555 as a continuation of the first. The lower halves of the alphabets are now shifted regularly, but the alphabets and the index letters are mixed by means of a mnemonic key phrase, which can be different with each correspondent.
```

ยังไม่ใช่ FLAG

KEY = AGFL

```txt
Ny dn nsozwjnonsb ctb di mnnotwt kjtkgj taojs mzhjdqj hmzino atw ocnsbn ymzt iny ity xmjfoz

Izmdsl ocj hjpwxz jk mdnytmt, ymz Qnlzieqk Roontx ggh hdkc xdocbdtikc sptx zxsdy

Xz vgh lzrhkke pzsxxhtztj su Qrzohk ck Kofkcere as it was originally described in 1553 by Giovan Battista Bellaso in his book La cifra del. Sig. Giovan Battista Bellaso

For the implementation of this cipher a table is formed by sliding the lower half of an ordinary alphabet for an apparently random number of places with respect to the upper halfpicoCTF{b311a50_0r_v1gn3r3_c1ph3rdb3eEcFa}

The first well-documented description of a polyalphabetic cipher however, was made around 1467 by Leon Battista Alberti.

The Vigenzlp Wjjsys cd niycygicy tixyucxyt wlfmyo niy Lfcycnj Xtmd ic Umvpluc Ncqbpl.

Jh 1508, Uiiuyhfm Eljnsyncfm jhgyonpx ubp mp-wlfmyo nbvffb lpwuu (l gbnccy iq micqnfx lfqblvfnd) niue qpowx mueys vp u dltnjwlf dixjphphu iq niy Gchyyymz Hnkcjw.

Wzqqvnt’x nzhtiy gtjfqjo vuuzvwjy ds 1555 fn v htionspvynji tk ocj kdmxy. Ocj qjrjw cvqazn tk ocj fgkmfwzyx vmj sjr xmdayjy mjlpgfwgt, gzo omj vgumvwjyn vsi ocj niyjc gzyyzmx fmz rnszi gt hjfin tk v hsjhjsnx fjd kcwfnz, bmdxm hvi gj ydkkzmjso rnyc zfhc xtwmzxujiijio.
```

```
picoCTF{b311a50_0r_v1gn3r3_c1ph3rdb3eEcFa}
```