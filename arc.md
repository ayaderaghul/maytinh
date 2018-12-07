---
description: Arc  
---

# Arc: Từ vựng, ngữ pháp, tinh thần 

Source: [Arc tutorial](http://www.arclanguage.org/tut.txt)

Tôi viết chương này độc lập với những chương trước, để người đọc nào tò mò mà nhảy vọt từ điểm ban đầu lên đây xem trước về Arc. Vì thế tôi nói lại nhiều khái niệm râu ria mà nếu các bạn đọc những chương trước rồi thì sẽ hiểu luôn và tiết kiệm công sức. Tuy nhiên, tôi vẫn muốn viết cho người chưa có khái niệm gì một bản mô tả khái quát về cốt lõi của ngôn ngữ lập trình này. Bởi vì nó xứng đáng đứng độc lập.

Người đọc muốn đi vào trọng tâm nhanh nhất có thể hình dung Arc là một người lữ hành đơn độc đi từ miền đất xa lạ tới, một linh hồn trong cái máy. Nhân vật này giao tiếp bằng ngôn ngữ Arc. Vì vậy khi bạn tò mò muốn nói chuyện với Arc bạn phải nói với họ bằng ngôn ngữ Arc của họ. Cách tiếp cận đơn giản nhất là thử nói những cái đơn giản và sau đó tìm hiểu xem Arc tư duy như thế nào. Nếu Arc tư duy giống chúng ta, thi thoảng chúng ta sẽ à lên thích thú khi nhận ra những nét tính cách của chính loài người được phản chiếu lại qua một mảnh linh hồn xa lạ. 

Về mặt kỹ thuật, cách nói chuyện ở đây là bạn gõ vào một cổng giao tiếp và Arc sẽ nghĩ và trả lời bạn. Cổng giao tiếp này gọi là giao diện REPL và tôi giải thích ở dưới. Tuy nhiên bạn có thể bỏ qua phần kỹ thuật đó và đọc tiếp xuống phần từ vựng của Arc. Khi đó bạn sẽ bắt đầu hiểu được người lạ Arc này giao tiếp và tư duy như thế nào. Nếu bạn đã đọc hết các chương trước rồi thì khi đến chương này bạn sẽ mở được REPL thật trên máy của mình và nói chuyện với Arc thật sự khi đọc theo văn bản này. Đến cuối chương này bạn sẽ viết được chương trình Arc thật sự.  


#### Cài đặt Arc 
* Cài Racket từ trang của ngôn ngữ [Racket](https://download.racket-lang.org/) 
* Download Arc từ trang http://www.arclanguage.org/arc3.2.tar và giải nén (bạn có làm được việc này bằng dòng lệnh trên terminal không?).
* Từ Terminal, ```cd``` vào thư mục vừa giải nén và gõ ```racket -f as.scm``` và bạn sẽ vào môi trường lập trình Arc

REPL nghĩa là Read-Evaluate-Print-Loop (Vòng lặp Đọc-Xử lý-In). Đây là một phương pháp hiện hình thành một cổng giao tiếp (*a method embodied in a terminal emulator*). Ví dụ tôi vào thư mục của Arc, ```Open in Terminal``` và gõ vào ```racket -f as.scm```, khi đó tôi sẽ được vào môi trường lập trình Arc, khi tôi gõ lệnh Arc vào thì máy sẽ đọc (```read```), sau đó máy sẽ nghĩ và thi hành (```evaluate```) sau đó in (```print```) kết quả ra màn hình cho tôi xem. Quá trình này sau đó lại tiếp tục. Vì thế mà gọi là vòng lặp (```loop```).

## Biểu ngữ
#### Số và dây chữ: Những biểu ngữ đơn giản nhất 
Khi bắt đầu học một ngôn ngữ mới, ta cần học những từ vựng đơn giản nhất. Một chương trình viết bằng ngôn ngữ Arc sẽ bao gồm các biểu ngữ (*expression*). Biểu ngữ là một cấu trúc ngữ pháp biểu thị một cái gì đó. Những biểu ngữ đơn giản nhất là số (*number*) và dây chữ (*string*). Một dây chữ nghĩa là một liên hoàn các chữ cái (*character*) bọc trong dấu ngoặc kép. Tôi lấy ví dụ số trước:

```
arc> 25
25
arc> 

```



{% exercise %}
Gõ thử vào dấu 3 chấm một số tự nhiên (xóa dấu ba chấm đi nhé):

{% initial %}
...

{% solution %}
assert(typeOf(x) == 'number');

{% context %}

{% endexercise %}


Khi bạn gõ vào số 25, biểu ngữ này sẽ được xử lý thành giá trị mà nó mang, trong trường hợp này là chính nó. Khi đó Arc sẽ trả về cho bạn số 25 ở màn hình. Sau khi in ra xong thì Arc nhảy sang dòng lệnh mới, đợi bạn gõ lệnh mới.  Hãy thử với dây chữ:

```
arc> "foo"
"foo"
arc>
```
Bạn có thể thấy Arc xử lý dây chữ cũng y như vậy. Xử lý thành chính dây chữ đó và trả về chính dây chữ đó.

#### Danh sách các biểu ngữ bọc trong ngoặc đơn: Câu đơn

Một danh sách chứa nhiều hơn một biểu ngữ và được bọc lại trong ngoặc đơn cũng được coi là một biểu ngữ. Có thể hiểu là một câu đơn. Ngữ pháp của câu đơn như sau: Thành phần đầu tiên của danh sách là một động từ (*function*), những thành phần còn lại là các danh từ chỉ vật. Để dễ hình dung, tôi sẽ nói một số câu tiếng Việt theo ngữ pháp Arc:

```
> (quét nhà)
> (làm toán tiếng-anh văn-học)
> (nếu lười 
	(viết chương-trình-giải-toán))
```
Các bạn có thể thấy rằng, câu đầu tiên mà tôi muốn biểu (vì thế mà gọi là biểu ngữ) là: bạn đi quét nhà đi. Biểu ngữ này là danh sách có hai thành phần: thành phần ```quét``` và thành phần ```nhà```. Arc sẽ xử lý câu này từ trái sang. Thành phần đầu tiên, ```quét``` sẽ được ngầm coi là động từ, và thành phần sau đó, ```nhà```, sẽ được coi là vật mà là động từ ```quét``` áp dụng lên. Tức là đi làm hành động ```quét``` cái ```nhà``` mau đi. Biểu tượng ```quét``` là để chỉ hành động như thế nào? Hay hành động như thế nào thì gọi là ```quét```. Cái này là ngầm hiểu, tức là tôi sẽ chỉ dạy bạn ```quét``` như thế nào trước đó rồi. Nếu tôi chưa, thì bạn sẽ bảo là ```quét``` chưa được định nghĩa. Tương tự, cái nhãn ```nhà``` là chỉ vật như thế nào? Ở đây ```nhà``` là sàn nhà, cái này cũng là được định nghĩa trước rồi. Tôi nhớ khi tôi ngồi không nhưng tò mò cầm sách lên thấy loằng ngoằng, cô hàng xóm sang chỉ cho tôi bảng chữ cái và cách đọc một lần. Sau đó tôi bắt đầu tự đọc. Tôi nhớ khi tôi mới biết đọc, tôi nhìn vào trang sách thấy toàn biểu tượng xa lạ, nhưng sau khi đánh vần xong, tự dưng thấy trong não mình hiện ra một thứ không gian kỳ quặc. Tôi nhìn ra xung quanh. Không gian này không có thật và chỉ có ở trong đầu mình thôi, và không gian này rất sống động. Nó ở đâu ra, tôi nhìn lại vào trang sách, ồ, những biểu tượng kỳ quặc này giả lập (*simulate*) không gian ma thuật đó trong đầu tôi. Ồ!.

Đến chỗ này, nếu các bạn vẫn thấy lạ là ngôn ngữ Arc này không giống như ngôn ngữ lập trình mà bạn tưởng tượng, tức là nhị phân và các thể loại khó hiểu đâu rồi, thì tôi nhắc lại là các bạn đang nghĩ đến ngôn ngữ tầm thấp. Ngôn ngữ tầm thấp nhất là nhị phân. Tức là ngôn ngữ này chỉ có 2 trạng thái: bật - tắt (thông tin về hai trạng thái này được ký hiệu lại, một cách hiệu quả, bằng số 0 và 1). Lưu ý nếu thông tin không được lưu lại hiệu quả ngay từ đầu, ví dụ nếu bạn chọn lưu bằng biểu tượng hình: như kiểu hai vạch chẵn-lẻ, hay biểu tượng màu đen-trắng, thì khi các ý nghĩ mà chúng ta cần biểu thị trở nên phức tạp hơn các ngôn ngữ ký hiệu đó sẽ nở bung ra rất nhiều và rất nhanh, ta sẽ gặp trở ngại rất lớn khi tìm cách biểu thị chính mình. Tôi lấy ví dụ lại, với một người lữ hành khác, đến từ miền đất khác, người xa lạ này nói ngôn ngữ nhị phân, tức là trong đầu cô ta, chỉ có một mạch điện với một công tắc và một bóng đèn. Khi công tắc đóng mạch, bóng đèn sáng, ta hiểu rằng cô ta đang muốn biểu thị ý tích cực, tức là "Đúng", khi công tắc chuyển sang hở mạch, bóng đèn tắt, ta hiểu rằng cô ta đang muốn biểu thị tiêu cực, tức là "Sai". Khi đó, ta sẽ chỉ hỏi được cô này những câu hỏi mang tính đúng-sai, đen-trắng, và có hai cực mà thôi. Cô yêu hay ghét, cô đồng ý hay không đồng ý, cô đi hay ở.. Bây giờ, nếu cô ta tự đi nâng cấp bản thân, cô ta lắp thêm hàng nghìn mạch bật-tắt như thế, khi đó, cô ta có khả năng giao tiếp một câu phức tạp hơn rất nhiều, nhưng khi cô ta mở mồm nói ra, sẽ chỉ toàn là ```bật tắt tắt tắt bật bật tắt..``` chả hạn. Nếu ta biểu thị các trạng thái này bằng số 0 và 1 thì những gì cô ta trả ra sẽ chỉ là một chuỗi ```0101010101011111000``` Ta làm thế nào để hiểu được dòng này? Các bạn có tin là ban đầu lập trình tức là viết nhị phân như thế này trực tiếp vào cái máy không? :D Các thẻ dập lỗ, một là dập, không là không dập, sau đó cho các thẻ này chạy qua các đầu đọc :D  Khi các cao thủ trở nên mệt mỏi với việc nói chuyện bằng ngôn ngữ nhị phân với cái máy, họ nghĩ ra cách tăng năng suất bằng cách đổi sang hệ bát phân. Tức là họ sẽ nói bằng ngôn ngữ bát phân, nhưng sẽ có chương trình dịch câu lệnh trong ngôn ngữ bát phân đó sang câu lệnh trong ngôn ngữ nhị phân cho cái máy tính hiểu :D Nghe thì không tưởng, nhưng các bạn thử tưởng tượng ngôn ngữ của chim chóc và các loài vật. Chúng có những ngôn ngữ tầm thấp của riêng chúng. Ví dụ, có những câu để gọi bạn tình, có những câu để báo hiệu nguy hiểm cho đồng loại. Hoặc ám hiệu khói của các bộ lạc, khi có chim sắt rơi trên bãi biển, thông tin đi nhanh và chi tiết hơn người đưa tin vượt đường rừng. Quay lại cách ký hiệu thông tin. Nếu ta ký hiệu bằng vạch chẵn lẻ, khi các vạch này đầy lên, nơ-ron bắt đầu nhìn ra những hình thù lờ mờ như sông núi thủy mặc. Qua 40 ngàn năm tiến hóa, tất nhiên nơ-ron nhìn ra ý nghĩa từ cái vô nghĩa. Tại sao? Bởi vì đó là chương trình sống còn viết bằng quá trình tiến hóa. Loài người cần ý thức giả lập này để điều khiển cơ thể vật lý này trong không gian. Khi ta chọn biểu tượng từa tựa cho sự vật để thể hiện sự vật, khi đó ngôn ngữ mà ta dùng chỉ định ý nghĩ mà ta nói. Ví dụ tôi muốn nói về sông núi, tôi phải tra trong đầu biểu tượng nào giống hình sông núi. Cái phần tra đó, tăng thêm khối lượng công việc cho bộ xử lý bé nhỏ của não. Nếu tôi dùng chữ "sông núi" để chỉ sông núi, và tất cả cùng đồng ý thì "sông núi" là chỉ sông núi, thì "sông núi" là sông núi. Còn nếu tất cả đồng ý "sông núi" là để chỉ đồng ruộng, thì khi đó "sông núi" là đồng ruộng. Ký hiệu "sông núi" không khiến cho đám nơ-ron sáng lên những ý kiến thêm không cần thiết. Tất nhiên, việc viết ý bằng hình không có gì sai, cũng có thể là một nhánh tiến hóa. Ở đâu đó trong vũ trụ có những nền văn minh tiến hóa theo con đường đó. Nhiều khi lịch sử chỉ là những lối rẽ ngẫu nhiên và thế giới, dù cho có bao nhiêu sự kiện đi chăng nữa, vĩnh viễn lạnh lùng.

Quay lại hệ nhị phân, sau khi các cao thủ mệt mỏi với hệ nhị phân, họ dịch sang bát phân. Sau bát phân thì là gì? Từ đó thế giới của các ngôn ngữ máy tính tiến hóa ra muôn hình muôn vẻ, nhưng nói chung ta có thể chia ra ngôn ngữ tầm thấp và tầm cao. Ngôn ngữ tầm thấp rất gần với ngôn ngữ máy tính. Ngôn ngữ tầm cao, có thêm khả năng chứa đựng tư duy trừu tượng, rất gần với ngôn ngữ và tư duy con người. Nói nôm na, ngôn ngữ là công cụ, và giới hạn của công cụ tôi dùng, là giới hạn của thế giới của tôi. Làm người, tôi muốn thế giới của mình rộng lớn, có thêm nhiều công cụ để biểu lộ bản thân. (Bởi vì tôi tin rằng mỗi người đều có tự do niềm tin, tự do biểu hiện, và quyền được sống trong một không gian lành mạnh trong thế giới này. Như mọi thứ khác). Và ngôn ngữ tầm cao là ngôn ngữ mạnh hơn ngôn ngữ tầm thấp rất nhiều, không chỉ bởi vì khi sử dụng ngôn ngữ tầm cao tôi có thể biểu đạt cùng một lượng thông tin nhanh hơn so với khi tôi nói câu đó trong ngôn ngữ tầm thấp, mà còn bởi vì khi sử dụng ngôn ngữ mang tính trừu tượng cao, tôi có thể biểu đạt thông tin ở một tầm hoàn toàn mới. Nếu bạn sử dụng ám hiệu khói, bạn có thể thấy rằng bạn gặp rắc rối với việc tự xuất bản tiểu thuyết của chính mình rất nhanh.

Tôi quay lại ví dụ tiếng việt để thể hiện ngữ pháp của Arc. 

```
> (quét nhà)
> (làm toán tiếng-anh văn-học)
> (nếu lười 
	(viết chương-trình-giải-toán))
```

Ta có thể thấy câu thứ hai ở đây có nhiều hơn một danh từ, ```toán```, ```tiếng-anh```, ```văn-học```. Những danh từ này chỉ môn học, và những môn học này sẽ được bỏ vào cùng một quá trình xử lý tên là ```làm```. Câu này có nghĩa là bạn đi ```làm``` môn ```toán```, môn ```tiếng-anh``` và môn ```văn-học``` đi. Bởi vì cả ba môn này cùng dùng động từ ```làm``` bạn sẽ thấy thật là tiện làm sao khi ta để động từ ```làm``` đứng ở đầu câu và các vật mà động từ đó cần xử lý sẽ đứng hết ở sau.

Ở câu thứ ba, tôi giới thiệu một dạng ngữ pháp phức tạp hơn, nhưng sẽ không đi sâu vào cho đến phần sau. Câu thứ ba rất đơn giản, ```nếu``` bạn ```lười``` là đúng, bạn sẽ ```viết``` một chương trình để giải toán thay cho mình.

Tôi quay lại với ngôn ngữ Arc thật sự, lấy ví dụ một biểu ngữ toán:

```
arc> (+ 1 2)
3
```

Arc xử lý biểu ngữ ```(+ 1 2)``` mà bạn gõ vào như sau: đầu tiên Arc sẽ xử lý ```+``` sau đó đến ```1``` sau đó đến ```2```. Biểu tượng ```+``` sẽ được xử lý (*hiểu*) là hàm cộng (phép tính cộng), biểu tượng ```1``` sẽ được hiểu là số 1, biểu tượng ```2``` sẽ được hiểu là số 2, sau đó số 1 và 2 sẽ được cho vào hàm cộng. Hàm cộng sẽ cộng hai số này lại với nhau. Giá trị trả về là số 3, vì thế Arc in ra màn hình cho bạn con số 3. 

(Macro là một thành phần bất hảo trong ngôn ngữ Arc, hắn tương tự như động từ (*function*), nhưng hắn thay đổi danh sách trước khi danh sách này được xử lý).

Lưu ý là biểu tượng ```+``` ở đây được định nghĩa từ trước (*built in*) cho Arc là phép cộng. Ta hoàn toàn có thể định nghĩa lại cho Arc hiểu là biểu tượng ```+``` dùng để chỉ phép nhân. Tôi sẽ hướng dẫn bạn cách định nghĩa lại này ở phần dưới khi ta học đến cách định nghĩa cho Arc từ vựng mới.

#### Biểu ngữ lồng trong biểu ngữ: Câu ghép 

Trong câu đơn ```(+ 1 2)``` bạn có thể thấy rằng ngoài thành phần thứ nhất là động từ, thì các thành phần còn lại chính là những biểu ngữ đơn giản nhất (các con số). Biểu ngữ đơn giản thì cũng là biểu ngữ, chứng tỏ rằng, các thành phần đó có thể được thay thế bằng các biểu ngữ phức tạp. Tức là ta lồng câu đơn vào thành câu ghép. Ví dụ:

```
arc> (+ 1 (* 3 4))
12
```
Ở ví dụ này, biểu ngữ ```2``` đã được thay bằng biểu ngữ ```(+ 3 4)```. Thế này nghĩa là gì? Nghĩa là hệ thống tư duy của Arc là theo vòng lặp (*recursively*) từ các cấu trúc rất đơn giản. Ở câu ghép này, Arc sẽ xử lý (*đọc*) từ trái sang, dấu ```+```, số ```1```, câu đơn ```(+ 3 4)```. Câu đơn ```(+ 3 4)``` sẽ được đánh vần tương tự từ trái sang: biểu tượng dấu ```*``` được hiểu là phép nhân. biểu tượng số ```3``` được hiểu là số 3 và biểu tượng số ```4``` được hiểu là số 4. Sau đó số 3 và 4 được cho vào dấu nhân để trả về kết quả 3 nhân 4 bằng 12. Arc tiếp tục ê a đánh vần tiếp câu đầu còn dang dở: giá trị số 1 và giá trị số 12 được cho vào động từ cộng để thực hiện phép cộng: một cộng mười hai bằng mười ba. Arc trả về giá trị 13.

## Biểu tượng và giá trị<a name="biểu-tượng-và-giá-trị">
Đến phần này bạn cần hiểu được sự khác nhau căn bản giữa hai khái niệm biểu tượng và giá trị. Biểu tượng là một thứ gì đó nhìn sờ thấy được. Giá trị là thứ tinh thần tinh túy không thấy được nhưng không có nghĩa là nó không tồn tại. Với nỗ lực ghi nhận và lưu giữ lại thế giới, ta sử dụng các biểu tượng để chỉ một giá trị nào đó. Sau đó có thể dùng cùng biểu tượng đó để chỉ giá trị khác. Hoặc biểu tượng đó có thể mất đi, nhưng giá trị là thứ độc lập với biểu tượng, không liên quan đến việc anh gán nó vào biểu tượng nào hay biểu tượng đó có mất đi hay không. 

Trong ngôn ngữ Arc, biểu tượng số dùng để chỉ các con số. Bạn không thể định nghĩa lại những biểu tượng số đó để nó mang nghĩa khác. Ngòai ra thì hầu hết các biểu tượng khác đều có thể được định nghĩa lại. Arc ép buộc bạn rất ít. Các biểu tượng dùng để chứa đựng các giá trị mà bạn muốn gán. Ví dụ:

```
arc> (= foo 13)
13
arc> foo 
13
```
Bạn sẽ thấy rằng biểu ngữ ```(= foo 13)``` là dòng lệnh bảo Arc rằng, hãy gán giá trị 13 vào biểu tượng foo. Khi ta gõ lại biểu tượng foo này thì Arc sẽ không trả về chính biểu tượng đó mà Arc trả về giá trị mà biểu tượng đó chứa đựng. Tức là hàm ý của biểu tượng đó. 

Để ngăn Arc xử lý biểu tượng đó và trả về giá trị, ta đặt dấu nháy đơn trước biểu tượng foo, khi đó Arc sẽ trả về biểu tượng foo.

```
arc> 'foo 
foo 
```

Sẽ có người đọc thấy kỳ quặc tại sao trong biểu ngữ ```(= foo 13)``` Arc lại không xử lý foo, nếu như cách nghĩ của Arc là xử lý từ trái sang? Nếu Arc xử lý từ trái sang thì Arc sẽ gặp foo và khi đó sẽ trả về lỗi, bởi vì Arc không biết từ foo đó bao giờ. Chưa ai định nghĩa cho Arc biết từ foo đó nghĩa là gì. Thực ra ở trong câu đó, hàm ```=``` là hàm đặc biệt, khác với động từ bình thường một chút, hàm ```=``` sẽ bỏ qua thành phần đứng ngay sau nó. Có những hàm khác cũng sẽ hành động tương tự. 

Hàm ```=``` có thể hiểu là hàm gán giá trị 13 cho biểu tượng foo. Hoặc gọi là hàm đặt tên foo cho giá trị 13. Sau khi đặt tên rồi, ta gọi lại tên foo thì Arc sẽ hiểu là giá trị 13, tất nhiên là trừ khi ta nháy đơn foo. Dấu nháy đơn sẽ luôn trả về cả câu như biểu tượng của nó là thế, tuyệt đối không xử lý và tìm hiểu ý nghĩa của cả câu là gì. Ví dụ:

```
arc> (+ 1 2)
3
arc> '(+ 1 2)
(+ 1 2)
```

Câu đầu tiên trả về số 3 nhưng câu thứ hai trả về danh sách với các biểu tượng +, 1 và 2. 

#### Xây dựng danh sách với cons
```cons``` là viết tắt của *constructor* (xây dựng). Hàm này dùng để kiến tạo danh sách. Ví dụ:

```
arc> (cons 'f '(a b))
(f a b)
```
Câu trên nghĩa là thêm biểu tượng f vào đầu danh sách có sẵn '(a b).

Hàm này không thay đổi danh sách ban đầu mà tạo ra một danh sách mới. Ví dụ, nếu tôi đặt tên danh sách '(a b) là x thì khi tôi thêm 'f vào bằng ```cons``` thì Arc trả về danh sách mới chứ không can thiệp trực tiếp vào danh sách x. Khi ta gọi lại x thì Arc vẫn trả về danh sách ban đầu.

```
arc> (= x '(a b))
(a b)
arc> (cons 'f x)
(f a b)
arc> x
(a b)

```
Như ta có thể thấy, ```cons``` là hàm bình thường, sẽ có những hàm khác có tính chất như ```=```, tức là can thiệp vào biểu tượng và thay đổi ý nghĩa mà biểu tượng đó biểu thị, ở những mức độ khác nhau. 

#### car và cdr và list 

```car``` trả về thành phần đầu tiên của một danh sách, ```cdr``` trả về danh sách đó trừ thành phần đầu tiên.

```
arc> (car '(a b c))
a
arc> (cdr '(a b c))
(b c)
```

Để tạo ra một danh sách, ta dùng ```list```, hàm này thực ra tạo ra list bằng cách dùng hàm ```cons``` lặp đi lặp lại, đặt từng thành phần một vào danh sách. 

```scheme
arc> (list 'a 1 "foo" '(b))                      
(a 1 "foo" (b))
arc> (cons 'a (cons 1 (cons "foo" (cons '(b) nil))))
(a 1 "foo" (b))
```

Chú ý rằng danh sách có thể chứa đựng thành phần của bất kỳ thể loại nào: biểu tượng 'a, số 1, dây chữ "foo", danh sách '(b) chứa biểu tượng 'b.

Đến đây bạn có thể thốt lên sao mà nhiều ngoặc thế kia. Không ai đọc code bằng ngoặc, khi bạn dùng phần mềm biên tập văn bản *text editor* Emacs (như đã giới thiệu ở phần trước, Emacs sẽ tự xuống dòng và căn chỉnh code của bạn rất dễ đọc. Bạn bỏ qua các dấu ngoặc và chỉ đọc chữ trong đó.

Đến đây, bạn đã biết thêm các hàm để chỉ vị trí trong danh sách, ví dụ ```car``` là chỉ vào vị trí của thành phần đầu tiên trong danh sách và lấy nó ra. Khi kết hợp với ```=```, ta có thể thay đổi giá trị của danh sách ở vị trí đầu tiên. Lấy ví dụ danh sách x.

```
arc> x
(a b)
arc> (= (car x) 'z)
z
arc> x
(z b)
```
Bạn có thể thấy là nội dung (giá trị) của danh sách x đã thực sự bị ```=``` thò tay vào và thay đổi, ở vị trí mà ```car``` chỉ đến: vị trí đầu tiên.

Trong ngôn ngữ kiểu này, danh sách cực kỳ hữu dụng bởi vì bạn có thể dùng danh sách để thể hiện bất cứ thứ gì. Danh sách có hai số có thể để chỉ tọa độ của một điểm trong không gian 2 chiều, hoặc có thể diễn giải ra thành những ý nghĩa khác nhau. Khi ta muốn có tọa độ ba điểm, ta chỉ cần đẩy thêm một số nữa vào danh sách, thế là ta có danh sách 3 tọa độ của 3 trục trong không gian 3 chiều.

Chính sự nhanh nhẹn đó khiến ngôn ngữ kiểu này có thể biến hóa khôn lường và trở thành bất cứ thứ công cụ gì mà bạn muốn. Cái hay nhất chính là danh sách cũng có thể dùng để thể hiện code. Tức là bạn có thể viết ra các chương trình mà sẽ sản xuất ra các chương trình khác. Toàn bộ ngôn ngữ Arc này được viết ra từ một tập hợp rất nhỏ các từ vựng ban đầu, sau đó sử dụng các ngữ pháp đơn giản như ta thấy ở trên, để tạo ra các câu đơn câu ghép và các chương trình phức tạp hơn rất nhiều. Ta xây ngôn ngữ từ dưới lên một cách có hệ thống. 

## Tạo động từ mới 

Ta đã thấy một số động từ/hàm (*function*) ví dụ ở trên như +, cons, car, cdr. Bạn có thể tự định nghĩa thêm các động từ mới để dạy cho Arc biết. Muốn tạo được từ vựng mới thì công cụ phải có khả năng gán giá trị cho biểu tượng. Muốn làm điều đó thì trong bộ công cụ phải có một công cụ có khả năng can thiệp vào và thay đổi nội dung (giá trị) của một biểu tượng. Khi có một công cụ như thế rồi, thì sẽ có khả năng tạo ra những công cụ mới phức tạp hơn sử dụng công cụ đơn giản đó, mà cũng can thiệp vào biểu tượng ở những tầng lớp nghĩa mới. Tuy nhiên, kiểu can thiệp này tôi giới hạn ở những thời điểm khởi đầu nhất định. Bình thường, khi tôi sử dụng các hàm và biến, tôi không thay đổi nội dung gốc của cái gì cả, tôi tạo ra cái mới. Ví dụ trong đoạn code sau, cons không can thiệp vào x, x vẫn là x:

```
arc> (= x '(1))
arc> (cons 2 x)
'(2 1)
arc> x
'(1)
```
Nếu bạn hỏi thế làm sao để lưu lại '(2 1) để dùng tiếp. Muốn vậy bạn hứng giá trị '(2 1) vào biểu tượng 'y. Khi giá trị được tạo ra mà không lưu lại, thì hắn tan biến:

```scheme
arc> (= x '(1))
arc> (= y (cons 2 x))
arc> x
'(1)
arc> y
'(2 1)
```
Tất nhiên nhiều khi giá trị tạo ra này ta cho ngay vào hàm khác thì không cần lưu lại. Nhưng nếu ta muốn lưu lâu dài, thì cần đặt tên cho hắn. Tôi luôn code kiểu này, tức là cái tôi muốn tạo ra là một phiên bản khác và nếu muốn thì tôi đặt tên cho cái mới đó, chứ không thay đổi nội dung gốc của danh sách cũ. Sử dụng hàm thay đổi nội dung gốc của một thứ (ví dụ danh sách) rất nguy hiểm, và gây nhiều hậu quả (chủ yếu là ngạc nhiên khó chịu do lỗi bừa bãi và không biết lỗi ở đâu ra). Khi bắt buộc phải làm thế, nhiều khi bạn sẽ không biết là chương trình của mình bắt đầu sai từ chỗ nào, khi đó bạn sẽ phải chèn một số hàm chuyên in kết quả ra màn hình vào giữa các chương trình để biết là chương trình của bạn chạy đến chỗ nào thì hỏng. Tôi sẽ nói về đám đó ở sau.

Tôi nói tiếp về việc tạo động từ mới. Để tạo động từ mới thì ngữ pháp như sau:

```racket
arc> (def average (x y) 
       (/ (+ x y) 2))
#<procedure: average>
arc> (average 2 4)
3

```

Động từ dùng để định nghĩa động từ mới gọi là ```def``` (*define*: định nghĩa). Ta định nghĩa biểu tượng ```average``` sao cho nó cư xử như một động từ: nó nhận vào hai số ở chỗ hai biến x y và xử lý như ta bảo ở trong phần thân định nghĩa: ```(/ (+ x y) 2)```. Câu này có nghĩa là ta cộng hai số lại và chia đôi. Lưu ý là động từ ```def``` cư xử như ```=```, hắn bỏ qua một số thành phần trong danh sách. Hắn không động vào và không tìm cách hiểu nghĩa những từ đó. Sau khi hắn định nghĩa xong, Arc có thêm một từ vựng mới là động từ: ```average```. Tức là trung bình, trung bình của 2 và 4 là 3. Thế là từ nay Arc đã biết tính trung bình cộng của hai số tự nhiên. 

Đến đây tôi sẽ chỉ cách định nghĩa lại cho Arc biết dấu ```+``` là để chỉ phép nhân. 

```
arc> (def + (x y) 
	    (* x y))
arc> (+ 2 3)
6
```

Bạn có thể thấy rằng cách định nghĩa động từ mới rất đơn giản. Ta gọi động từ ```def``` lên, sau đó viết tiếp biểu tượng mà ta muốn sử dụng, ở đây là dấu ```+```, sau đó ta viết số lượng biến mà động từ này sẽ nhận vào: 2 biến x và y (nếu bạn nghĩ sao lại chỉ có 2 biến, tôi sẽ chỉ cách để nhận số lượng biến vô hạn ở dưới ;-). Thế là xong phần đầu, phần thân ta viết một biểu ngữ xử lý hai biến x và y này theo ý ta muốn. Ý ta muốn ở đây là nhân hai biến này với nhau. Vì thế, sau khi định nghĩa xong, khi ta hỏi lại Arc rằng ```(+ 2 3)``` trả về gì, Arc sẽ mang nhân 2 với 3 và trả về 6. Ta tẩy não con bé rồi.

Động từ ```def``` không có gì đặc biệt, hắn gọi động từ ```=``` lên để gán một hàm vào một biểu tượng cho sẵn. Câu ```def``` ở trên chính là câu sau:

```
arc> (= average (fn (x y) (/ (+ x y) 2)))
arc> (average 2 4)
3
```
Ở đây ```average``` được gán hàm/động từ ```(fn (x y) (/ (+ x y) 2))```. Hàm này nếu đứng không ```(fn (x y) (/ (+ x y) 2))``` thì là hàm không tên. Không vấn đề gì, hàm không tên vẫn hoạt động như thường. Khi bạn hiểu một ý tưởng gì đó, mà chưa nghĩ ra được tên để gán cho nó, đám nơ-ron ở trung tâm ngôn ngữ trong não bạn chưa báo ra được một từ cụ thể để gán cho ý tưởng đó. Không sao cả, nó vẫn hoạt động bình thường, nếu bạn giữ nó không tên. Ở đây cũng vậy, khi bạn bê nguyên hàm không tên kia vào một biểu ngữ, để vào đúng vị trí mà nó vẫn để, tức là vị trí đầu tiên trong danh sách, thì nó vẫn nhận vào các biến đứng sau và hoạt động bình thường. Không có gì sai trái. Ví dụ:

```
arc> ((fn (x y) (/ (+ x y) 2)) 2 4)
3
```
Biểu ngữ này là danh sách có 3 thành phần: một hàm trả về trung bình cộng, số 2 và số 4. Khi Arc xử lý xong ba thành phần này, và cho hai thành phần cuối vào thành phần ban đầu, tức là cho số 2 và 4 vào hàm trung bình cộng, thì giá trị trả về là số 3.

#### Một trường hợp đặc biệt 
Như các bạn đã thấy ở trên, ngữ pháp của một biểu ngữ là ```(động-từ vật-1 vật-2 vật-3..)```. Tuy nhiên có một trường hợp đặc biệt, khi thành phần đầu tiên trong danh sách không phải là động từ mà là một dạng tổ chức dữ liệu (*data structure*). Tôi dịch tạm, ai nghĩ ra từ khác tốt hơn cần nói ra. Một tổ chức dữ liệu là một dạng danh sách chứa đựng các thành phần dữ liệu. Tôi lấy ví dụ  danh sách ```'(1 2 3)``` là một tổ chức dữ liệu, bởi vì danh sách này chứa các thành phần nhỏ hơn. Các thành phần nhỏ hơn này là các đơn vị dữ liệu. Một ví dụ khác về một tổ chức dữ liệu là dây chữ ```"foo"```. Dây chữ này là một biểu ngữ đơn giản, và trông như một khối thống nhất. Nhưng thực ra dây chữ này là một dây các chữ cái, tức là hắn là một tổ chức dữ liệu bao gồm các thành phần dữ liệu nhỏ hơn. Hắn được cấu thành từ 3 đơn vị dữ liệu là 3 chữ cái f, o và o. 

Tôi nói tiếp về trường hợp đặc biệt này của ngữ pháp Arc, khi thành phần đầu tiên của biểu ngữ là một tổ chức dữ liệu, thì tiếp sau đó là một số đếm chỉ vị trí. Khi đó Arc sẽ dùng số đếm chỉ vị trí này để truy nhập vào tổ chức dữ liệu kia và trả về cho bạn đơn vị dữ liệu ở vị trí tương ứng. Nếu số đếm chỉ vị trí đó vượt ra ngoài độ dài của tổ chức dữ liệu, Arc sẽ báo lỗi. Lưu ý là trong khoa học máy tính, người ta thường đếm từ số 0. Ví dụ:

```
arc> ('(1 2 3) 0)
1
arc> ('(1 2 3) 3)
Error
arc> ("foo" 1)
#\o 
```

Ở ví dụ trên, trong câu thứ nhất, Arc tìm đến vị trí số 0 của danh sách '(1 2 3) và trả về đơn vị dữ liệu ở vị trí đó, tức là số 1. Trong câu thứ hai, Arc tìm đến vị trí số 3, vị trí này nằm ngoài danh sách, vì vậy Arc báo lỗi. Trong câu thứ 3, Arc tìm đến vị trí số 1 của tổ chức dây chữ, và trả về chữ cái ```#\o``` ở vị trí số 1 đó. Trông hơi kỳ quặc nhưng đó là cách chữ cái được biểu thị trong ngôn ngữ Arc, để phân biệt với biểu tượng ```'o```. 

#### Loại
Có thể bạn thấy hơi ngạc nhiên khi chữ cái ```#\o``` lại khác với biểu tượng ```'o```. Trong ngôn ngữ Arc, các đơn vị dữ liệu được phân loại ra thành các loại (*type*) khác nhau. Mỗi loại sẽ có nét tính cách riêng. Tôi liệt kê ra một số loại ta đã gặp: động từ (*function*), số (*number*), dây chữ (*string*), biểu tượng (*symbol*), chữ cái (*character*), danh sách (*list*). Arc có một hàm chuyên để trả về loại của các đơn vị dữ liệu. Tức là khi bạn đưa một đơn vị dữ liệu bất kỳ cho hàm đó, hàm đó sẽ trả về loại của dữ liệu đó. Trước khi tôi nói, bạn có đoán được hàm đó là gì không? Tôi gợi ý là ngôn ngữ Arc rất hợp với cách nghĩ tự nhiên của con người. Và Arc cũng khuyến khích người ta phát triển khả năng suy nghĩ tự nhiên (*intuitive*) và logic đó. Tôi nghĩ nếu bạn đọc và hiểu Arc đến đây rồi, bạn sẽ đoán đúng. Hàm đó là ```type```. Ví dụ:

```
arc> (type +)
fn                     => function / hàm 
arc> (type 1)
int                    => integer / số tự nhiên  
arc> (type "foo")
string                 => string / dây chữ 
arc> (type 'o)
sym                    => symbol / biểu tượng 
arc> (type #\o)
char                   => character / chữ cái  
arc> (type '(1 2))
cons                   => constructor / list / danh sách  
```

#### Ví dụ thêm về hàm ```=```

Ta đã thấy ở trên về việc hàm ```=``` có thể can thiệp và thay đổi giá trị của một biểu tượng. Sau khi có thêm cách mới để chỉ đến một vị trí trong tổ chức dữ liệu, tôi lấy thêm ví dụ về việc hàm ```=``` có thể can thiệp vào tổ chức dữ liệu bằng những cách khác nhau như thế nào:

```
; Ban đầu biểu tượng x chưa có gía trị gì.
arc> (= x 2)
; Bây giờ biểu tượng x đã có giá trị 2
arc> x
2

; Ta dùng hàm = để tiếp tục can thiệp 
arc> (= x 3)
; Bây giờ biểu tượng x đã có giá trị 3
arc> x
3

; Biểu tượng + được định nghĩa trước cho Arc là phép cộng 
arc> (+ 2 3)
5
; Ta can thiệp vào biểu tượng +
arc> (= + (fn (x y) (* x y)))
; Bây giờ Arc đã hiểu + là phép nhân 
arc> (+ 2 3)
6

; Cho một tổ chức dữ liệu 
arc> (= s "foo")
arc> s
"foo"

; Can thiệp vào tổ chức dữ liệu này bằng cách chỉ định vị trí  
arc> (= (car s) #\m)
; (car s) tức là chỉ vào vị trí đầu tiên của dây chữ s 
; "foo" đã thành "moo"
arc> s
"moo"

; Ta vừa học thêm một ngữ pháp đặc biệt dùng để chỉ định vị trí 
; vị trí đầu tiên : ("foo" 0) hoặc (s 0)
arc> (= (s 0) #\f)
; "moo" trở lại thành "foo"
arc> s
"foo"

```

#### Gán tạm 

Hàm ```=``` hoặc hàm ```def``` sẽ gán gía trị vào biểu tượng mãi, tức là x sẽ mang giá trị 2 cho đến hết chương trình nếu không có gì thay đổi. Tuy nhiên có cách để gán tạm, tức là x mang giá trị 2 chỉ ở trong giới hạn một biểu ngữ (một chương trình nhỏ) mà thôi. Ngoài đó ra thì x không mang giá trị 2. Đó là hàm ```let``` để gán tạm một biến, hàm ```with``` để gán tạm nhiều biến. Ví dụ:

```
arc> (let x 1
	   (+ x (* x 2)))
3
arc> (with (x 3 y 4)
	   (sqrt (+ (expt x 2) (expt y 2))))
5
```
Tôi nghĩ ngay cả khi tôi chưa nói gì cả, các bạn chỉ cần đọc phương trình này, là đã có thể hiểu được phương trình này viết cái gì. Trong câu thứ nhất: Với x = 1, lấy x cộng với 2x. Kết quả là 3

Câu thứ hai cũng vậy. Trước tiên, hãy nhìn vào các từ vựng và đoán: ```sqrt``` là *squareroot* tức là căn bậc 2. ```expt``` là *exponent* tức là mũ. Nếu ta lấy x mũ 2 cộng với y mũ 2 rồi khai căn bậc hai của kết quả đó, thì ta được cái gì? Đây chính là công thức tính đường chéo của một tam giác vuông. Với x bằng 3 và y bằng 4, đường chéo của tam giác vuông là 5. 

```
(với (x 3 y 4)
	(căn hai (cộng (mũ x 2) (mũ y 2))))
```
Hóa ra Arc cũng được dạy trước một ít toán. Nếu ta thấy Arc chưa biết gì thì ta nhớ ra là Arc có sẵn công cụ để ta có thể dạy cho Arc học thêm.

Bạn có nhớ ví dụ sau không:

```
(quét nhà)
(làm toán văn tiếng-anh)
(nếu lười 
	(viết chương-trình-tính-đường-chéo-tam-giác-vuông))
```

Tôi bảo bạn đi quét nhà đi, sau đó làm toán văn tiếng anh, và nếu lười thì viết một chương trình nhỏ để tính đường chéo của tam giác vuông. Tất nhiên sau khi tôi viết chương trình tính đường chéo của tam giác vuông để tăng khả năng lập trình, tôi vẫn tự tính đường chéo của tam giác vuông bằng mồm và tay để tăng khả năng tính nhẩm. Tôi đã nói rồi, muốn chạy đua với chính mình, cái gì *có thể* thì *phải* làm.

#### in 

Ví dụ khi ta định nghĩa hàm ```average``` ta muốn hàm này in ra biến mà hắn nhận vào trước khi in ra kết quả, ta chèn vào một biểu ngữ chuyên để in. Hàm để in là ```pr``` hoặc ```prn```. pr là *print* và prn là *print \n*. Trong khoa học máy tính, ```\n``` là dấu xuống dòng. prn tức là in ra kết quả và sau đó xuống dòng. 

```
arc> (def average (x y)
       (prn "my arguments were: " (list x y))
       (/ (+ x y) 2))

arc> (average 100 200)
my arguments were: (100 200)
150
```

## Câu điều kiện<a name="câu-điều-kiện">

Trong ngôn ngữ Arc, tất nhiên có câu điều kiện, bởi vì cuộc đời này nó thế. Nếu chưa có, hẳn sẽ đến lúc người lập trình tự thấy cần thiết mà viết thêm vào cho Arc hiểu. ```if``` (*nếu*) giống ```=``` và ```def``` ở chỗ hắn không xử lý hết tất cả các biến hắn ngậm vào. Khi được đưa cho 3 biến, hắn sẽ xử lý biến đầu tiên, nếu đúng, hắn trả về giá trị của biến số 2, nếu sai, hắn trả về giá trị của biến số 3.

```
arc> (if (odd 1) 'a 'b)
a
arc> (if (odd 2) 'a 'b)
b 
```

Các bạn chỉ cần đọc qua 2 câu trên là đã hiểu được: Nếu số 1 là lẻ (giá trị của biểu ngữ (odd 1) là đúng) thì trả về biểu tượng a nếu không thì trả về biểu tượng b. Bởi vì số 1 là số lẻ thật (đúng) cho nên trả về biểu tượng a. Bây giờ ta nói câu tương tự, nhưng thay số 1 bằng số 2, khi đó giá trị của biểu ngữ (odd 2) là sai, do đó Arc trả về biểu tượng b.

Các bạn có thể hỏi: Thế nào là *đúng*? Đúng nghĩa là khi ta xử lý biểu ngữ đó, biểu ngữ đó trả về một giá trị nào đó ngoại trừ ```nil```. ```nil``` là không có gì, là sai, là không có giá trị. Tức là chỉ cần biểu ngữ đó trả về giá trị bất kỳ, thì đã là đúng rồi. Đối với Arc, tất cả mọi giá trị đều là *đúng*. Thứ duy nhất sai trong thế giới của Arc là ```nil```, tức là sai chính nó.

Về mặt kỹ thuật, ```nil``` vừa là sai vừa là danh sách rỗng. ```t``` là đúng. Nhưng cái gì có giá trị thì cũng đều là đúng hết.

```
arc> (odd 1)
t
arc> (odd 2)
nil
```
Đến đây các bạn có thể hỏi, liệu danh sách rỗng có phải là sai không? Nếu các bạn nghĩ theo kiểu tập hợp trong toán học, thì tập hợp rỗng là sai, là không phải tập hợp.

Ngữ pháp của Arc khá linh hoạt khi nói đến câu điều kiện, ví dụ:

```
arc> (if (odd 2) 'a)
nil         => khi chỉ có hai biến, biến thứ ba ngầm định là nil 
```

Khi bạn muốn viết các câu đơn if lồng vào nhau:

```
(if a b c d e)
```

chính là viết tắt của:

```
(if a 
	b
	(if c
		d 
		e))
```

Mỗi biến mà ```if``` nhận vào đều là một biểu ngữ duy nhất, nếu bạn muốn có các biểu ngữ chạy nối tiếp nhau (không phải câu ghép mà là hai câu đơn nối tiếp nhau), bạn có thể dùng ```do```. *do* nghĩa là làm.

```
arc> (do (prn "hello") 
         (+ 2 3))                             
hello
5
```

Trong câu trên, Arc in ra dây chữ "hello" sau đó hắn làm tính 2 cộng 3 bằng 5. Tôi đã bảo rồi, bạn đi ```(làm toán văn-học)``` đi :D 

Nếu bạn chỉ muốn một số biểu ngữ được chạy khi điều kiện trả về đúng, bạn có thể dùng cấu trúc sau: if với do và bỏ biến cuối:

```
(if a
    (do b
        c))
```
Tuy nhiên tình huống này quá phổ biến, cho nên Arc tiến hóa thêm hẳn một hàm riêng để chỉ tình huống đó 

```
(when a
  b
  c)
```
Câu trên nghĩa là ```khi a đúng, làm b và c```. Lưu ý là ban đầu Arc không cần có từ vựng ```when``` trong từ điển, trong quá trình tiến hóa, tác giả viết thêm từ vựng đó cho Arc sử dụng chính những công cụ trên. Ta sẽ thử định nghĩa ```when``` ở phần sau.

#### and và or 

Hàm ```and``` (*và*) và ```or``` (*hoặc*) giống như câu điều kiện bởi vì chúng không xử lý nhiều biến hơn cần thiết. 

* ```and``` là hàm tìm ```nil```. Khi ta cho ```and``` n biến, hắn xử lý lần lượt từ trái sang, nếu hắn bắt gặp ```nil``` hắn sẽ dừng xử lý ngay lập tức và trả về ```nil```. Nếu hắn đi hết các biến rồi mà không thấy nil hắn trả về giá trị cuối cùng.

* ```or``` là hàm tìm giá trị (giá trị tức là không phải ```nil```). Nếu cho hắn n biến, hắn đi từ trái sang, khi bắt gặp giá trị, hắn dừng ngay lập tức và trả về giá trị đó. Nếu hắn đi hết hàng rồi mà không gặp giá trị nào (toàn ```nil```) hắn trả về ```nil```.

Hai hàm này có ích ở chỗ, nhiều khi ta muốn đi tìm một thứ gì đó trong một danh sách bất định. Và ta chỉ muốn hắn đi tìm giá trị đầu tiên thôi, còn lại nếu hắn đi xa hơn vùng hắn cần thiết, lỗi sẽ xảy ra và hỏng chương trình.

#### no

Hàm ```no``` nhận vào duy nhất 1 biến. Hắn trả về ```t``` nếu biến đó là ```nil```, còn lại nếu ta đưa cho hắn giá trị, thì hắn trả về ```nil```. Hàm này nôm na là hàm phản giá trị. Đưa đúng thì hắn bảo sai, đưa sai bảo đúng. Thằng này bảo đông đi tây và bảo tây đi đông.

## Lặp chính nó<a name="lặp-chính-nó"> 

Đây là một mục rất quan trọng. Quan trọng gần nhất của lối nghĩ có phương pháp. (Rất Arc, rất LISP và rất *functional programming*). Bạn hãy nghĩ đến phương pháp quy nạp, ta bắt đầu từ điểm đầu là điểm dễ nhất không cần chứng minh, sau đó ta chứng minh rằng điểm ngay cạnh nó là đúng, khi đó ta có thể tiếp tục quy nạp vô hạn về phía sau. Khi cô giáo giảng cho bạn về phép toán đó ở lớp 5, bạn vô cùng thích thú. Đến lớp 12, khi cô giáo giảng lại về phép quy nạp đó, bạn bĩu môi (vì bạn thấy người ta bĩu môi) "Ôi dào, ra đời chả ai dùng quy nạp trong thực tế cuộc sống". Tôi có dùng. Khi bạn nghĩ đến những tình huống mà dữ liệu bắt đầu bằng một điểm ban đầu dễ hiểu, sau đó lặp dần lên đến vô hạn, thì chương trình mà bạn viết ra cũng cần phải phản ánh điều đó. Cấu trúc của dữ liệu sẽ quyết định cấu trúc của hàm bạn cần viết ra để xử lý dữ liệu đó. 

Tôi lấy ví dụ, bạn muốn viết một hàm đo độ dài của một danh sách. Bạn viết được tiêu đề của hàm đó như sau:


```
(def mylen (xs)
 ...)

```

* Lưu ý ```xs``` ở đây không phải để chỉ 1 biến mà là 1 danh sách biến.
* Đầu tiên bạn nghĩ về trường hợp dễ ẹc của dữ liệu, đó là khi danh sách đó là danh sách rỗng 
* Sau đó bạn lại nghĩ, thế nhưng lại sẽ có những danh sách chứa đựng một độ dài bất định các thành phần. Phải làm sao?

Đến đây thì bạn hiểu rằng dữ liệu của bạn có 2 trường hợp, một là danh sách rỗng, hai là danh sách khác rỗng. Lối nghĩ này bảo bạn dùng ```if``` - hàm điều kiện có hai mệnh đề 

```
(def mylen (xs)
	(if (no xs)
		...))
```

* Lưu ý ```(no xs)``` sẽ trả về ```t``` nếu danh sách rỗng. 
* Khi đó, kết quả của trường hợp dễ ẹc là 0. Bởi vì danh sách rỗng thì tức là độ dài của danh sách bằng 0.

```
(def mylen (xs)
	(if (no xs)
		0
		...))
```

Đến đây thì bạn thấy trường hợp thứ 2 phức tạp hơn, đó là danh sách khác rỗng, nhưng độ dài bất kỳ. Phải làm thế nào? Lẽ tự nhiên bạn sẽ nghĩ, ta đếm từng thành phần một. Đếm thế nào? Người chăn cừu có một cái túi sỏi, mỗi khi anh ta lùa một con cừu vào chuồng thì anh ta bỏ ra đất một hòn sỏi. Đến khi cừu vào hết thì hết sỏi. Nếu có ngày hết cừu mà chưa hết sỏi thì khá gay. Hoặc nếu có ngày hết sỏi mà chưa hết cừu thì cũng không phải là bình thường. Lưu ý là ở đây anh ta không cần biết đếm từ 1 đến 10.

Sau khi từ biệt người chăn cừu và trở về từ giữa dãy Alpes hùng vĩ, hãy sử dụng phương pháp những hòn sỏi của anh chăn cừu. Hãy tưởng tượng rằng danh sách mà ta cần biết độ dài là một đàn cừu, và ta dùng các viên sỏi để *số hóa* đám cừu. 

* Để sự đếm xảy ra, đầu tiên ta phải có cách để đủn một chú cừu vào chuồng trước. Một thôi. Phương pháp đơn giản nhất nào để trích xuất thành phần đầu tiên ra khỏi danh sách? ```car``` ạ. Lưu ý là ```car``` là một trong những từ vựng đầu tiên. Nếu bạn muốn định nghĩa ```first``` bạn sẽ dùng ```car```. Tập hợp những từ vựng ban đầu của LISP gồm có vỏn vẹn 6 từ thì phải.

* Sau khi ủn một bác, bạn cần phải bỏ ra một hòn sỏi. Sau đó thì bạn nhận ra rằng, ồ, kể từ đây ta chỉ cần lặp đi lặp lại chuỗi hành động này thôi. Cứ ủn một em thì bỏ một sỏi. Cứ như vậy cho đến hết. Tức là bạn sẽ thấy rằng trong trường hợp thứ 2 này, ta có thể sử dụng vòng lặp để biểu hiện toàn bộ quá trình hành động. Nghe cũng giống quy nạp nhỉ. 

* Nghĩ tự do bằng ngôn ngữ của ta một lúc ta bắt đầu nghĩ bằng ngôn ngữ Arc. Khi chuồng chưa có cừu, số đếm mặc định là số 0 (câu này thể hiện ở dòng ```(if (no xs) 0```. Vậy khi có 1 cừu vào chuồng, số đếm sẽ tự động tăng thêm 1. Và ta áp dụng quá trình đó vào đám cừu còn lại. Bạn có thể hình dung rằng hàm bạn viết để thể hiện điều đó sẽ như sau:

```
.. + 1 ..  (car xs) ..    => cừu đầu tiên 
       ..  (cdr xs) ..    => đám cừu còn-lại 

```
Lưu ý ta đang viết chính xác những gì ta nghĩ. ```car``` chính là đầu tiên và ```cdr``` chính là còn-lại.

* Nhìn vào bản nháp code của bạn, đến đây thì ta làm gì? Hãy nhìn vào bản nháp đó và xem ta có thể làm gì với những thành phần gì. Ví dụ ta sẽ làm gì với ```(cdr xs)```? Ồ, ta cần phải đo độ dài của danh sách ```(cdr xs)```. Tức là ta cần phải thực hiện hành động đếm-cừu lên đám-cừu-đó. Bạn nghĩ xem bạn đã có hàm nào để thực hiện hành động đo độ dài của một danh sách chưa? Câu trả lời là có. Đó chính là hàm mà bạn đang tìm cách viết, hàm bạn đặt tên là ```mylen```. Hãy tin tôi. Hãy sử dụng hàm đó vào code của bạn:

```
(def mylen (xs)
	(if (no xs)
		0
		( .. + 1 .. (car xs) ..
		         .. (mylen (cdr xs)) ..)))
```

* Đến đây bạn sẽ thấy rằng mylen sẽ xử lý ```(cdr xs)``` bằng cách mở ra một câu điều kiện: nếu ```(cdr xs)``` rỗng thì trả về 0, nếu không thì tiếp tục làm gì đó và đo độ dài của ```(cdr (cdr xs))```. Độ dài của ```(cdr xs)``` cũng như ```xs``` là bất định, nhưng hãy tự do cho mình đi đến điểm cuối của danh sách đó, khi mà hắn có 0 thành phần. Khi đó thì sao?
  * Khi đó ```(mylen nil)``` sẽ trả về giá trị 0. 
  * Ta đi đến điểm còn 1 cừu ở ngoài chuồng, tức là danh sách có 1 cừu. Khi đó ```(mylen xs) = (+ 1 (mylen nil))```

Đây là hàm hoàn chỉnh:

```
(def mylen (xs)
	(if (no xs)
		0
		(+ 1 (mylen (cdr xs)))))
```
Đọc hàm trên như sau: Nếu danh sách rỗng thì trả về 0. Nếu không thì trả về một cộng với độ dài của đám-còn-lại. Nói bằng một thứ ngôn ngữ nửa Arc nửa ta: Nếu danh sách ```nil```, thì trả về 0, nếu không thì trả về nhiều hơn 1 của độ dài của ```cdr``` của danh sách.

```
arc> (mylen nil)
0
arc> (mylen '(a b))
2
```

#### So sánh 

Để so sánh với chính nó, so sánh dây chữ..

```
arc> (is 'a 'a)
t
arc> (is "foo" "foo")
t
arc> (let x (list 'a) 
       (is x x))
t
```

Để so giữa hai danh sách ta dùng iso (*isomorphic*)

```
arc> (iso (list 'a) (list 'a))
t
```
Để biết một biến có nằm trong các khả năng cho sẵn không 

```
arc> (let x 'a   
       (in x 'a 'b 'c))
t
```

Trường hợp:

```
arc> (def translate (sym)
       (case sym
         apple 'mela 
         onion 'cipolla
               'che?))
#<procedure: translate>
arc> (translate 'apple)
mela
arc> (translate 'syzygy)
che?
```

#### Các kiểu lặp khác 
Đây là những kiểu lặp mà không phải gọi lại chính nó trong bản thân định nghĩa của nó.

Làm gì đó khi x ở trong giới hạn cho phép:

```
arc> (for i 1 10 
       (pr i " "))
1 2 3 4 5 6 7 8 9 10 nil

arc> (each x '(a b c d e) 
       (pr x " "))
a b c d e nil
```
Những chương trình này in ra thành phần trong danh sách bằng pr, nhưng nil là giá trị mà chúng trả về.

Khi điều kiện gì đó còn đúng thì còn làm:

```
arc> (let x 10
       (while (> x 5)
         (= x (- x 1))
         (pr x)))
98765nil
```

(Hàm để làm cho đến khi điều kiện gì đó xuất hiện là ```until```)

Làm cái gì đó n lần:

```
arc> (repeat 5 (pr "la "))
la la la la la nil
```

#### map 

Ngoài các kiểu lặp trên, có những hàm có khả năng thao tác trên dữ liệu một cách mạnh mẽ, toàn diện và có hệ thống.

```map``` sẽ áp dụng một hàm lên toàn bộ danh sách:

```
arc> (map (fn (x) (+ x 10)) '(1 2 3))
(11 12 13)
```

Nếu ta cho ```map``` cùng lúc nhiều danh sách, hắn sẽ áp dụng lên hết cho đến khi hết danh sách ngắn nhất.

```
arc> (map + '(1 2 3 4) '(100 200 300))
(101 202 303)
```

Với hàm chỉ có 1 biến, ta thể có viết tắt: ```[... _ ...] = (fn (_) (... _ ...))```

```
arc> (map [+ _ 10] '(1 2 3))
(11 12 13)
```

``` 
Trong toán học: f.g(x) = f(g(x))
Trong Arc: (foo:bar x y) = (foo (bar x y)) 
```

```
arc> (map odd:car '((1 2) (4 5) (7 9)))
(t nil t)
```
Phản một hàm 

```
arc> (map ~odd '(1 2 3 4 5)) 
(nil t nil t nil)
```

Tự đọc những hàm sau:

```
arc> (keep odd '(1 2 3 4 5 6 7))
(1 3 5 7)
arc> (rem odd '(1 2 3 4 5 6))
(2 4 6)
arc> (all odd '(1 3 5 7))
t
arc> (some even '(1 3 5 7))
nil
arc> (pos even '(1 2 3 4 5))
1
arc> (trues [if (odd _) (+ _ 10)] 
            '(1 2 3 4 5))
(11 13 15)
```

Câu sau có gì khác biệt?

```
arc> (rem 'a '(a b a c u s))
(b c u s)

arc> (rem #\a "abacus")
"bcus"
```
#### sort 

```
arc> (sort < '(2 9 3 7 5 1))
(1 2 3 5 7 9)
arc> (insort < 4 x)
(1 2 3 4 5 7 9)
arc> x
(1 2 3 4 5 7 9)

arc> (sort (fn (x y) (< (len x) (len y)))
           '("orange" "pea" "apricot" "apple"))
("pea" "apple" "orange" "apricot")

arc> (sort (compare < len)
           '("orange" "pea" "apricot" "apple"))
("pea" "apple" "orange" "apricot")
```

## Số lượng biến bất định<a name="số-lượng-biến-bất-định">
Khi định nghĩa một hàm mới, các bạn đã gặp hai trường hợp ký hiệu biến như sau:

```
* fn (x y) ...     => Đây là khi hàm số nhận vào đúng 2 biến  
* fn (xs)  ...     => Đây là khi hàm nhận vào một danh sách, số lượng biến bất kỳ 
```
Ta sẽ xem xét tiếp các trường hợp mà hàm nhận vào số lượng biến không cố định:

* Có thể có thêm biến hoặc không 

Hàm ```greet``` sau nhất định nhận vào 1 biến, ví dụ ```'joe```. Có thể là chỉ có một biến đó thôi, hoặc có thể là thêm một biến nữa là dấu ```!```

```
arc> (def greet (name (o punc))
       (string "hello " name punc))
#<procedure: greet>
arc> (greet 'joe)
"hello joe"
arc> (greet 'joe #\!)
"hello joe!"
```
Một trường hợp phức tạp hơn:
```
arc> (def greet (name (o punc (case name who #\? #\!)))
       (string "hello " name punc)) 
*** redefining greet
#<procedure: greet>
arc> (greet 'who)
"hello who?"
```

* Khi ta viết ```(x y . z)``` nghĩa là hàm này nhận vào x và y sau đó nhận thêm số lượng biến bất kỳ. Trong phần thân của hàm, x và y được xử lý trước, sau đó toàn bộ các biến còn lại được cho vào một danh sách.

```
arc> (def foo (x y . z) 
       (list x y z))
#<procedure: foo>
arc> (foo (+ 1 2) (+ 3 4) (+ 5 6) (+ 7 8))
(3 7 (11 15))
```

* Nếu bạn muốn hàm nhận vào số lượng biến bất kỳ và tất cả các biến được xử lý như nhau (phần sau không bị bỏ vào danh sách), bạn viết cấu trúc như sau:

```
fn xs ... thay vì fn (xs) ...
```

* Để áp dụng một hàm lên toàn bộ danh sách, ta dùng ```apply```

```
arc> (apply + '(1 2 3))
6
```

Đến đây thì ta có thể viết hàm ```average``` mà có thể nhận số lượng biến bất kỳ. 

```
arc> (def average args 
       (/ (apply + args) (len args)))
#<procedure: average>
arc> (average 1 2 3)
2
```
Tương tự như vậy, bạn có định nghĩa lại được dấu ```+``` thành phép nhân với số lượng biến bất kỳ được không.

## Lặt vặt<a name="lặt-vặt">

Danh sách kiểu này giống như từ điển: một từ khóa gắn với một giá trị tương ứng.

```
arc> (= codes '(("Boston" bos) ("Paris" cdg) ("San Francisco" sfo)))
(("Boston" bos) ("Paris" cdg) ("San Francisco" sfo))

arc> (alref codes "Boston")
bos
```

* Dây chữ 

```
arc> (string 99 " bottles of " 'bee #\r)
"99 bottles of beer"

arc> (tostring                  
       (prn "domesday")
       (prn "book"))
"domesday\nbook\n"
```

* coerce

```
arc> (map type (list 'foo 23 23.5 '(a) nil car "foo" #\a))
(sym int num cons sym fn string char)
arc> (coerce #\A 'int)
65
arc> (coerce "foo" 'cons)
(#\f #\o #\o)
arc> (coerce "99" 'int)
99
arc> (coerce "99" 'int 16)
153
```

* Nếu bạn tưởng tượng danh sách giống như một giá để bày đồ đạc. Động từ ```push``` là để chèn thêm một thành mới lên đầu giá, và động từ ```pop``` là để bỏ đi thành phần cuối giá.


```
arc> (= x '(c a b))
(c a b)
arc> (pop x)
c
arc> x
(a b)
arc> (push 'f x)
(f a b)
arc> x
(f a b)
```


```
arc> (push 'l (cdr x))
(l a b)
arc> x
(f l a b)
```

* Cộng 1 và bớt 1 

```
arc> (let x '(1 2 3) 
       (++ (car x))
       x)           
(2 2 3)
```
* zap 

Ta đã gặp rất nhiều hàm can thiệp và thay đổi giá trị mà một biểu tượng đang nắm giữ, giờ ta sẽ gặp một hàm chung chung cho ý tưởng đó. Hàm ```zap``` gán giá trị trả về vào biểu tượng ban đầu.

```
(++ x)  =  (zap [+ _ 1] x)
```
