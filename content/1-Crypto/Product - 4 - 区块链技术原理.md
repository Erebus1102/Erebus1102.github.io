# 1 . 密码学原理
>[!info] 按照计算机出现前后划分为古典密码学 Classical Cryptography 和现代密码学 Modern Cryptography，其中从古代到近代大概可划分为 7 代加密法
## Gen 1 - 隐藏法 Concealment Method
> 🍋
## Gen 2 - 凯撒加密法 Caesar Cipher
> 是一种单表代换密码，加密方式就是通过对字母的位移进行加密，比如把字母表右移三位，上面是明文表，下面是对应的密文表。如下图所示：
> ![[content/notes/images/Pasted image 20230702125611.png]]
## Gen 3 - Vigenère cipher
## Gen 4 - Enigma cipher
## Gen 5 - Lucifer cipher [现代密码学的开端](https://zh.wikipedia.org/wiki/分组密码)
## Gen 6 - RSA
>RSA 算法是第一个公钥密码算法，也是第一个数字签名算法。具有乘法同态性，也可以称为第一个乘法同态特性的算法，它被提出的时间最早，关于它的研究最为广泛，因此也是理论上最成熟的密码学算法。算法如下：

KeyGen:
1. 选择需要保密的大素数 $p, q$
2. 计算 $n = p*q,\phi (n)=(p-1)(q-1)$
3. 选择一个整数 $e$ 满足 $1<e<\phi(n),且gcd(e,\phi(n))=1$
4. 计算 $e$，满足 $e*d=1\ mod\ \phi(n)$
5. 公钥是 $\{e,n\}$, 私钥是 ${d}$
Encrypt：
$$
c = m^e
$$
Decrypt:
$$
m = c^{d}=m^{ed}=m^{k\phi(n)+1}
$$
乘法的同态性：
$$
\begin{gather}
c_{1}= m^e_1,c_{2}= m^e_2\\
c_{1}*c_{2}= m^e_1*m^e_2=(m_1*m_2)^e
\end{gather}
$$
Sign:
$$
\sigma = hash(m)^d,签名是(\sigma,m)
$$
Verify:
$$
\sigma^e? = hash(m)
$$


## Gen 7 - Quantum encryption

>公钥密码的数学基础 
- 费马大定理：1637 年费马提出费马猜想： $x^{n}+y^{n}=z^{n}，当n>2时这个方程式有整数解$，这个猜想和哥德巴赫猜想、四色猜想共同被称为数学界的三大猜想。费马猜想在 1994 年被数学家安德鲁怀尔斯和他的学生理查泰勒证明，因此他们两人也获得了数学界的诺贝尔奖——Fields Medal。
- 费马小定理：$若 P 为素数、则对所有的整数 a 有：a^{p} = a\ mod\ p$
- 欧拉定理：$若\ gcd (k, n) = 1，则\  k^{\phi (n))} = 1\ mod\ n$
- 群论：1830 年又法国数学家伽罗瓦创立，1846 年由刘维尔代发表，群论的概念如下：
		- 群论是一种代数结构，代数结构就是有若干集合，比如群: $（G，*）$
		- 群的成立需要有以下四个性质
			- 封闭性：群中任意两个元素经过\*运算后，结果仍然是群中的元素
			- 结合律：$(a*b)*c = a*(b*c)$
			- 单位元：存在单位元（幺元），与任何元素相乘，结果不变；
			- 逆元：每个元素都存在逆元，元素与其逆元相乘，得到幺元
	
---
# 2 . Basic principles of mnemonic words
---


---
BackLink: [[content/1-Crypto/0. Crypto Index|Crypto Index]]
