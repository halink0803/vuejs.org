---
title: So sánh với những framework khác
type: guide
order: 801
---

Đây chắc chắc là trang khó nhất để viết trong toàn bộ phần hướng dẫn này, nhưng chúng tôi cảm thấy nó quan trọng. Có điều chắc chắn là, bạn có các vấn đề bạn đã cố gắng giải quyết và sử dụng một thư viện khác để làm việc đó. Bạn ở đây bởi vì bạn muốn biết xem Vue có thể giải quyết chúng tốt hơn không. Và đó là cái mà chúng tôi hi vọng sẽ cho bạn câu trả lời.

Chúng tôi cũng rất cố gắng để tránh thiên vị. Là những thành viên chính, chúng tôi chắc chắc thích Vue rất nhiều. Có những vấn đề chúng tôi nghĩ Vue giải quyết tốt hơn bất cứ thư viện nào khác. Nếu chúng tôi không tin tưởng vào điều đó, chúng tôi sẽ không tiếp tục xây dụng Vue. Mặc dù vậy, chúng tôi cũng muốn sự công bằng và chính xác. Khi những thư viện khác cung cấp những lợi ích đáng kể, ví dụ như hệ sinh thái đồ sộ các renderer thay thế của React hay việc Knockout hỗ trợ trình duyệt tới tận IE6, chúng tôi cũng cố gắng liệt kê chúng.

Chúng tôi cũng muốn **các bạn** giúp cho tài liệu này được cập nhật bởi vì "thế giới" JavaScript phát triển rất nhanh! Nếu bạn nhận ra một sự thiếu chính xác hoặc một cái gì đó có vẻ không đúng, vui lòng cho chúng tôi biết bằng việc [mở một issue](https://github.com/vuejs/vuejs.org/issues/new?title=Inaccuracy+in+comparisons+guide).

## React

React và Vue chia sẻ nhiều điểm tương đồng. Cả 2 đều:

- sử dụng một virtual DOM()
- Cung cấp các view component có thể tương tác và xây dựng được.
- Tập trung duy trì phần lõi của thư viện, với những tính năng ví dụ như routing(điều hướng) và quản lý trạng thái toàn cục được giải quyết bằng các thư viện hỗ trợ

Do rất giống nhau trên nhiều khía cạnh, chúng tôi đã dành nhiều thời gian hơn để điều chỉnh phần so sánh này nhiều hơn các phần khác. Chúng tôi muốn chắn chắn rằng không chỉ có sự chính xác về kĩ thuật, mà còn cân bằng về nội dung. Chúng tôi chỉ ra những điểu mà React vượt trội hơn Vue, ví dụ như sự đa dạng của hệ sinh thái của họ và sự phong phú của những renderer đặc trưng.

Nói như vậy, nó là không thể tránh khỏi sự so sánh này sẽ có thiên vị cho Vue đói với một vài người dùng React, do có rất nhiều chủ đề được tìm hiểu ở đây một cách nào đó khách quan. Chúng tôi công nhận sự tồn tại những sở thích kỹ thuật khác nhau và bài so sánh này trước hết nhằm vào những lý do chính tại sao Vue tiềm năng là một sự lựa chọn phù hợp tốt hơn nếu sở thích của bạn trùng hợp với chúng tôi.

Cộng đồng của React [](https://github.com/vuejs/vuejs.org/issues/364) trong việc giúp đỡ chúng tôi đạt được độ cân bằng này, cảm ơn đặc biệt Dan Abramov từ đội React. Anh ấy đã vô cùng hào phóng với thời gian và chuyên môn của anh ấy để giúp đỡ chúng tôi điều chỉnh tải liệu này cho đến khi cả hai bên [đều hài lòng](https://github.com/vuejs/vuejs.org/issues/364#issuecomment-244575740) với kết quả cuối cùng.

### Hiệu suất

Cả React và Vue đều cung cấp một hiệu suất khá tương đồng trong hầu hết các tình huống sử dụng, và Vue thường nhanh hơn một chút nhờ vào việc cài đặt được một Virtual DOM nhẹ hơn. Nếu bạn có hứng thú với các con số thì [3rd party benchmark](https://rawgit.com/krausest/js-framework-benchmark/master/webdriver-ts/table.html) cung cấp số liệu hiệu suất tập trung vào raw rendering/updating. Lưu ý rằng số liệu kia không tính đến các trường hợp cấu trúc component phức tạp, do đó các bạn chỉ nên lấy nó để tham khảo chứ nó không phải đánh giá chính thức về hiệu suất.

#### Nỗ lực tối ưu

Trong React, khi state của một component thay đổi, nó sẽ render lại toàn bộ component phụ, bắt đầu từ component đó như là gốc. Để tránh việc render lại component con một cách không cần thiết, bạn hoặc là phải sử dụng `PureComponent` hoặc cài đặt `shouldComponentUpdate` khi có thể. Bạn có thể cũng cần phải sử dụng cấu trúc dữ liệu không thay đổi để làm cho việc thay đổi state dễ dàng tối ưu. Tuy nhiên, trong những trường hợp cụ thể, bạn không thể nào tin tưởng vào vào những sự tối ưu đó bởi vì `PureComponent/shouldComponentUpdate` giả sử rằng toàn bộ đầu ra của cây phụ được xác định bởi những thuộc tính (props) của component hiện tại. Nếu không trong trường hợp đó, thì sự tối ưu hóa này có thể dẫn tới sự không ổn định trạng thái của DOM.

Trong Vue, những dependencies của một component được tự động theo dõi khi nó được render, nhờ đó hệ thống biết chính xác component nào thực sự cần được render lại khi có thay đổi về trạng thái. Mỗi component có thể được hiểu là tự động có `shouldComponentUpdate` được cài đặt sẵn cho bạn mà không cần thông báo những component lồng nhau(???).

Nói chung việc này giúp lập trình viên không cần phải lo về việc tối ưu hóa hiệu suất của class, và cho phép họ tập trung hơn vào việc xây dựng ứng dụng cũng như mở rộng nó.

### HTML & CSS

Trong React, tất cả mọi thứ đều là JavaScript. Không những cấu trúc HTML được biểu diễn qua JSX, mà một số xu hướng gần đây đưa phần quản lý CSS vào bên trong JavaScript nữa. Cách tiếp cận này có những lợi ích của nó, nhưng đồng thời cũng phải trả giá mà có vẻ là không đáng cho tất cả mọi nhà phát triển.

Vue dựa vào những công nghệ web cổ điển và xây dựng trên chúng. Để chỉ cho bạn nó có nghĩa là như thế nào, chúng tôi sẽ đi sâu ào một vài ví dụ.

#### JSX với Templates

Trong React, tất cả component biểu diễn giao diện với các render function sử dụng JSX, một kiểu cú pháp khai báo giống như XML mà tương thích với JavaScript.

Các function render với JSX có một số lợi ích:

- Bạn có thể tận dụng sức mạnh của toàn bộ ngôn ngữ lập trình (JavaScript) để xây dựng view. Việc này bao gồm biến cục bộ, quản lý luồn và tham chiếu trực tiếp các giá trị JavaScript trong phạm vi.

- Các công cụ hỗ trợ (ví dụ: linting, kiểm tra kiểu, gợi ý trong trình biên soạn) cho JSX đang tiên tiến hơn những gì đang sẵn có cho Vue template.

Trong Vue, chúng tôi cũng có các [render function](render-function.html) và thậm chí [hỗ trợ JSX](render-function.html#JSX), bởi vì thỉnh thoảng bạn cần khả năng đó. Tuy nhiên, trải nghiệm mặc định chúng tôi cung cấp template như là một sự thay thế đơn giản hơn. Bất cứ cú pháp html hợp lệ nào cũng hợp lệ trong Vue template, việc này mang đến một số những lợi ích của nó:

- Với nhiều nhà phát triển, những người đã và đang làm việc với HTML, template cho cảm giác tự nhiên hơn để đọc và viết. Lợi thế này bản thân nó có vẻ hơi chủ quan, nhưng nếu nó giúp cho lập trình viên hiệu quả hơn thì lợi ích của nó là khách quan.

- Những template dựa trên HTML giúp cho nó dễ dàng hơn để chuyển những ứng dụng có sẵn sang Vue với những lợi thế về tương tác.

- Việc này cũng làm dễ dàng hơn cho người thiết kế và những lập trình viên ít kinh nghiệm có thể chuyển đổi và đóng góp vào trong codebase.

- Bạn thậm chí có thể sử dụng những bộ biên tập trước (pre-processors) như Pug (trước đây được biết đến với tên Jade) để tạo Vue template của bạn.

Một số người cho rằng bạn cần phải học thêm DSL(Domain-Specific Language - Ngôn ngữ cụ thể miền) để có thể viết các template - chúng tôi tin là sự khác biệt này là hời hợt nhất. Đầu tiên, JSX không có nghĩa là người dùng không cần phải học gì cả - nó là những cú pháp bổ sung trên nền của JavaScript thuần, do đó nó có thể dễ dàng cho một số người quen thuộc với JavaScript để học, nhưng nói rằng nó 'miễn phí' là sai lầm. Tương tự như vậy, một template chỉ là những cú pháp bổ sung trên nền HTML thuần và do đó tốn rất ít để học cho những ai đã quen thuộc với HTML. Với DSL chúng tôi cũng có thể giúp người dùng đạt được nhiều hơn với ít code hơn (ví dụ: cú pháp `v-on`). Những tính năng tương tự có thể liên quan đến nhiều code hơn khi sử dụng JSX thuần hoặc render function.

Ở một cấp cao hơn, chúng ta có thể chia component thành 2 loại: component hiển thị và component logic. Chúng tôi khuyến khích sử dụng template cho những component hiển thị và render function / JSX cho những component logic. Tỉ lệ phần trăm những component này phụ thuộc vào loại app mà bạn đang xây dựng, nhưng nhìn chung chúng tôi thấy component hiển thị phổ biến hơn rất nhiều.

#### CSS phạm vi component (Component-Scoped CSS)

Trừ khi bạn chia components ra thành nhiều files (ví dụ với [CSS Modules](https://github.com/gajus/react-css-modules)), giới hạn CSS trong React thường được thực hiện với giải pháp CSS-in-JS (ví dụ: [styled-components](https://github.com/styled-components/styled-components), [glamorous](https://github.com/paypal/glamorous), và [emotion](https://github.com/emotion-js/emotion)). Điều này mở ra một phương pháp styling hướng theo component khác với quy trình viết CSS thông thường. Thêm vào đó, mặc dù có những cách để nén CSS vào trong một file stylesheet khi build, nhưng nó vẫn phổ biến là khi chạy bạn cần thêm nhiều file để style làm việc một cách chính xác.

Nếu bạn là một fan của CSS-in-JS, có nhiều thư viện CSS-in-JS hỗ trợ Vue (ví dụ: [styled-components-vue](https://github.com/styled-components/vue-styled-components) và [vue-emotion](https://github.com/egoist/vue-emotion)). Khác biệt lớn nhất giữa React và Vue ở đây là phương pháp style mặc định của Vue giống với thẻ `style` trong [single-file-components](single-file-components.html)

[Single-file components](single-file-components.html) cho bạn khả năng truy cập tới CSS trong cùng một file như với phần còn lại của code component.

``` html
<style scoped>
  @media (min-width: 250px) {
    .list-container:hover {
      background: orange;
    }
  }
</style>
```

Thuộc tính tùy chọn `scoped` sẽ tự động giới hạn CSS này chỉ trong component của bạn bằng việc thêm một thuộc tính duy nhất (ví dụ như `data-v-21e5b78`) vào và dịch `list-containter:hover` thành kiểu như `.list-containter[data-v-21e5b78]:hover`

Cuối cùng, styling trong một file (single-file) của Vue rất linh hoạt. Thông qua [vue-loader](https://github.com/vuejs/vue-loader), bạn có thể sử dụng bất cứ một trình dịch trước(preprocessor), dịch sau(post-processor), và thậm chí có thể tích hợp sâu với [CSS Modules](https://vue-loader.vuejs.org/en/features/css-modules.html) -- tất cả chỉ với `<style>`.

### Scale - Phạm vi

#### Scaling Up - Mở rộng

Cho những ứng dụng lớn, cả Vue và React đều cung cấp những giải pháp điều hướng (routing) thiết thực. Cộng đồng React cũng rất sáng tạo trong các giải pháp quản quản lý trạng thái (ví dụ: Flux/Redux). Những mô hình quản lý trạng thái và [thậm chí chính Redux](https://github.com/egoist/revue) có thể dễ dàng tích hợp vào những ứng dụng Vue. Không những thế, Vue còn còn thể áp dụng mô hình này một bước xa hơn với [Vuex](https://github.com/vuejs/vuex), một giải pháp quản lý trạng thái lấy cảm hứng từ Elm mà tích hợp sâu vào trong Vue mà chúng tôi cho là cung cấp một trải nghiệp phát triển tốt hơn.

Một điểm khác biệt quan trọng nữa giữa những đề xuất này là những thư viện quản lý trạng thái và điều hướng của Vue (giữa [những mối quan tâm khác](https://github.com/vuejs)) được hỗ trợ chính thức và cập nhật mới nhất cùng với thư viện chính. React thay vào đó lựa chọn để những vấn đề này cho cộng đồng, tạo ra một hệ sinh thái phân mảnh hơn. Là một framework nổi tiếng hơn, hệ sinh thái của React giàu có hơn rõ rệt so với Vue.

Cuối cùng, Vue cung cấp một [dự án CLI generator](https://github.com/vuejs/vue-cli) cho phép bạn có thể dễ dàng bắt dầu một project mới với tùy chọn hệ thống xây dựng, bao gồm [webpack](https://github.com/vuejs-templates/webpack), [Browserify](https://github.com/vuejs-templates/browserify), hoặc thậm chí [không có hệ thống build](https://github.com/vuejs-templates/simple). React cũng có [create-react-app](https://github.com/facebookincubator/create-react-app), nhưng hiện tại nó đang có một vài hạn chế:

- Nó không cho phép bất cứ lựa chọn cài đặt nào trong quá trình sinh dự án, trong khi các mẫu dự án của Vue cho phép thay đổi như là [Yeoman](http://yeoman.io/)

- Nó chỉ cung cấp một template đơn cho bạn xây dựng một ứng dụng đơn trang, trong khi Vue cung cấp rất rộng và đa dạng những template cho những mục đích và hệ thống xây dựng khác nhau.

- It cannot generate projects from user-built templates, which can be especially useful for enterprise environments with pre-established conventions.

Nó là quan trọng để lưu ý là rất nhiều những hạn chế này là chủ ý thiết kế của nhóm phát triển create-react-app và chúng thực sự có những lợi thế. Ví dụ, chừng nào mà dự án của bạn cần thật đơn giản, và bạn không bao giờ cần "eject" để thay đổi quá trình xây dựng của bạn, bạn sẽ có thể cập nhật nó như là một điều kiện tiên quyết. Bạn có thể đọc thêm về [khác biệt triết lý tại đây](https://github.com/facebookincubator/create-react-app#philosophy)

#### Scaling Down - Thu hẹp

React nổi tiếng vì việc học khó của nó. Trước khi bạn có thể bắt đầu, bạn cần phải biết về JSX và có thể cả ES2015+, từ rất nhiều ví dụ sử dụng cú pháp class của React. Bạn cũng sẽ phải học về các hệ thống build, bởi vì cho dù bạn có thể về mặt kĩ thuật sử dụng độc lập Babel để dịch trực tiếp code của bạn trên trình duyệt, thì nó cũng hoàn toàn không phù hợp cho sản phẩm cuối cùng.

Trong khi Vue mở rộng tốt ngang, nếu không nói là tốt hơn React, Vue có thể thu hẹp lại như jQuery. Đúng vậy - tất cả những gì bạn phải làm là đặt một thẻ scrip vào trong một trang:

``` html
<script src="https://cdn.jsdelivr.net/npm/vue"></script>
```

Sau đó bạn có thể bắt đầu viết code Vue và thậm chí ra mắt một phiên bản nén nhỏ cho sản phẩm mà không phải cảm thấy tội lỗi hoặc lo lắng về những vấn đề hiệu suất.

Do bạn không cần phải biết về JSX, ES2015 hoặc hệ thống xây dựng để bắt đầu với Vue, nó chỉ khiến các lập trình viên trung bình ít hơn một ngày đọc [hướng dẫn](./) để có thể có đủ khả năng xây dựng một ứng dụng không vớ vẩn.

### Native Rendering

React Native cho phép bạn có thể viết những ứng dụng native cho iOS và Android sử dụng những mô hình component của React. Điều là là rất tuyệt cho các lập trình viên, bạn có thể áp dụng kiến thức của một framework cho nhiều nền tảng. Trong mảng này, Vue có một sự hợp tác chính thức với [Weex](https://alibaba.github.io/weex/), một UI framework cho nhiều nền tảng được phát triển bởi Tập đoàn Alibaba, sử dụng Vue với vai trò là runtime JavaScript framework. Điều này có nghĩa với Weex, bạn có thể sử dụng cú pháp Vue component để viết các component mà không những có thể render trên trình duyệt, mà còn cón thể render native trên iOS và Android.

Vào thời điểm hiện tại, Weex vẫn đang được tích cực phát triển và chưa được hoàn thiện và có thể cạnh tranh với React Native, nhưng sự phát triển của Weex được hướng bởi nhu cầu thực tế của thị trường thương mại điện tử lớn nhất trên thế giới, và đội phát triển Vue sẽ tích cực hợp tác với đội phát triển Weex để chắc chắn có một trải nghiệm mượt mà cho những lập trình viên Vue.

Một sự lựa chọn khác cho các nhà phát triển Vue sẽ có là [NativeScript](https://www.nativescript.org/), thông qua một [plugin được cộng đồng xây dựng](https://github.com/rigor789/nativescript-vue)

### With MobX - Với MobX

MobX trở nên khá phổ biến trong cộng đồng React và it thực sự sử dụng một hệ thống tương tác giống như Vue. Trong một giới hạn, React + MobX workflow có thể xem là một phiên bản của Vue, do đó nếu bạn đang sử dụng sự kết hợp đó và thích nó, thì việc chuyển sang Vue có thể là một bước hợp logic.

## AngularJS (Angular 1)

Một vài cú pháp của Vue trông sẽ rất giống với AngularJS (ví dụ: `v-if` với `ng-if`). Bởi vì AngularJS có rất nhiều thứ đúng đắn đã là nguồn cảm hứng cho Vue trong những ngày đầu phát triển. Tuy nhiên cũng có rất nhiều những hạn chế của AngularJS mà Vue cố gắng cải thiện một cách tốt hơn.

### Độ phức tạp

Vue thì đơn giản hơn AngularJS, bao gồm cả API và thiết kế. Thời gian học đủ để xây dựng một ứng dụng không vớ vẩn thường chỉ mất ít hơn một ngày, với AngularJS thì không thể.

### Độ linh hoạt và tính module

AngularJS có những quan điểm mạnh mẽ về việc ứng dụng của bạn nên được cấu trúc như thế nào, trong khi Vue thì linh hoạt hơn. Trong khi Vue có thể thích nghi với nhiều kiểu dự án khác nhau, chúng tôi cũng nhận ra rằng đôi khi sẽ có ích hơn nếu quyết định thay cho bạn, nhờ thế bạn có thể chỉ cần bắt tay vào code.

Đó là lý do tại sao chúng tôi cung cấp một [webpack template](https://github.com/vuejs-templates/webpack) mà bạn có thể cài đặt trong vài phút, đồng thời cũng cho phép bạn truy cập vào những tính năng cao cấp như hot module reloading, lintin, CSS extraction, và nhiều hơn nữa.

### Data binding

AngularJS sử dụng binding hai chiều giữa các scope, trong khi Vue ép vào luồng dữ liệu một chiều giữa các component. Điều này làm cho luồng dữ liệu dễ dàng để suy luận cho những ứng dụng không đơn giản.

### Directives vs Components

Vue có sự phân định rạch ròi giữa directive và component. Directive chỉ được dùng để đóng gói sự mô phỏng DOM, trong khi component là những đơn vị có đầy đủ view và logic dữ liệu. Trong AngularJS, có rất nhiều sự không rõ ràng giữa directive và component.

### Hiệu suất

Vue có hiệu suất tốt hơn và dễ dàng hơn rất nhiều để tối ưu bởi vì nó không sử dụng 'dirty checking'. AngularJS trở nên slow khi nó sử dụng rất nhiều watcher, bởi bất cứ khi nào phạm vi thay đổi, tất cả watcher cần phải được đánh giá lại lần nữa. Hơn thế nữa, chu trình xử lý (digest cycle) có thể sẽ phải chạy nhiều lần để "ổn định" nếu có một vài watcher bật một cập nhật khác. Người dùng AngularJS thường phải dùng những phương pháp riêng để lách qua chu trình xử lý, và trong một vài tình huống, thì không có cách nào để tối ưu một phạm vi có nhiều watcher.

Vue không phải chịu đựng những hạn chế trên bởi vì nó sử dụng một hệ thống giám sát yêu cầu trong suốt với hàng đợi bất đồng bộ - tất cả những thay đổi được bật/tắt độc lập trừ khi chúng có quan hệ phụ thuộc rõ ràng.

Thú vị là có nhiều điểm tương đồng trong cách mà Angular và Vue đang tiếp cận các vấn đề này của AngularJS.

## Angular (Từng được biết đến là Angular 2)

Chúng tôi có một phần riêng dành cho Angular mới bởi vì nó thực sự là một framework mới hoàn toàn so với AngularJS. Ví dụ, nó đề cao một hệ thống first-class component, nhiều chi tiết cài đặt được viết lại hoàn toàn, và API cũng được thay đổi rõ rệt.

### TypeScript

Angular về cơ bản yêu cầu sử dụng TypeScript, bằng chứng là hầu hết tất cả tài liệu hướng dẫn và học tập đều dựa trên TypeScript. TypeScript có cho mình những lợi ích - kiểm tra kiểu tĩnh sẽ rất có ích cho những ứng dụng quy mô lớn, và có thể làm tăng hiệu quả làm việc cho những developer có nền tảng với Java và C#.

Tuy nhiên, không phải tất cả mọi người đều muốn sử dụng TypeScript. Trong nhiều trường hợp những ứng dụng nhỏ, việc có một hệ thống kiểu có thể gấy rối trí nhiều hơn là hiệu quả. Trong những trường hợp đó, bạn tốt nhất nên dùng Vue, bởi vì sử dụng Angular mà không có TypeScript có thể khá thử thách.

Cuối cùng, mặc dù không tích hợp sâu với TypeScript như Angular, Vue cũng cung cấp [các kiểu chính thức](https://github.com/vuejs/vue/tree/dev/types) và [decorator chính thức](https://github.com/vuejs/vue-class-component) cho những ai ước rằng có thể sử dụng TypeScript với Vue. Chúng tôi cũng tích cực hợp tác với nhóm làm TypeScript và VSCode của Microsoft để nâng cao trải nghiệm của TS/IDE cho Vue và người dùng TypeScript.

### Kích thước và hiệu suát

Nhắc đến hiệu suất, cả 2 framework đều rất nhanh và không có đủ dữ liệu từ thực tế để có thể xác định rõ ràng. Tuy nhiên, nếu các bạn muốn thấy một vài con số, Vue 2.0 dường như đang dẫn trước so với Angular theo như [3rd party benchmark](http://stefankrause.net/js-frameworks-benchmark4/webdriver-ts/table.html).

Các phiên bản gần đây của Angular, với [AOT compilation](https://en.wikipedia.org/wiki/Ahead-of-time_compilation) và [tree-shaking](https://en.wikipedia.org/wiki/Tree_shaking), giúp cho kích thước của Angular giảm đáng kể. Tuy nhiên, một dự án đầy đủ tính năng của Vue 2 với Vuex + Vue Router (~30KB gzipped) vẫn nhẹ hơn nhiều so với một ứng dụng AOT-compiled được sinh tự động bởi `angular-cli` (~130KB gzipped).

### Độ linh hoạt

Vue ít cứng nhắc hơn nhiều so với Angular, với việc hỗ trợ chính thức cho nhiều hệ xây dựng khác nhau và không có một giới hạn nào trong việc bạn cấu trúc ứng dụng của mình. Nhiều nhà phát triển thích sự tự do này, trong khi những người khác thì thích chỉ có duy nhất một cách đúng để xây dựng ứng dụng.

### Lộ trình học tập

Để bắt đầu với Vue, tất cả những gì bạn cần là quen thuộc với HTML và ES5 JavaScript (ví dụ: JavaScript thuần). Với những kĩ năng cơ bản này, bạn có thể bắt đầu xây dựng một ứng dụng hẳn hỏi với ít hơn một ngày ngồi đọc [hướng dẫn](./).

Đường học tập của Angular thì khó hơn. API bên ngoài của framework đồ sộ và một người dùng như bạn sẽ cần phải làm quen với rất nhiều những khái niệm trước khi có thể hiệu quả. Sự phức tạp của Angular phần nhiều là do mục đích thiết kế của nó là chỉ nhắm vào những ứng dụng lớn và phức tạp - nhưng nó làm cho framework trở nên khó cho những lập trình viên ít kinh nghiệm để lựa chọn.

## Ember

Ember là một framework đầy đủ tính năng, [is designed to be highly opinionated]. Nó cung cấp rất nhiều quy ước và một khi bạn đã quen với chúng, nó có thể giúp bạn làm việc rất hiệu quả. Tuy nhiên, điều đó cũng có nghĩa là bạn phải học rất nhiều và hi sinh sự linh hoạt. Nó là một cuộc đánh đổi khi bạn chọn giữa một framework cấu trúc và một thư viện với một tập hợp các công cụ làm việc với nhau. Sự lựa chọn sau cho bạn nhiều tự do hơn nhưng cũng yêu cầu bạn đưa ra nhiều quyết định cấu trúc hơn.

Do vậy, sẽ là hợp lý hơn nếu so sánh Vue core với những lớp Ember [template](https://guides.emberjs.com/v2.10.0/templates/handlebars-basics/) và [mô hình đối tượng](https://guides.emberjs.com/v2.10.0/object-model/):

- Vue cung cấp những tương tác kín trên những đối tượng JavaScript thuần và được tính toán tự động những thuộc tính. Trong Ember, bạn cần phải bọc mọi thứ trong những đối tượng Ember và khai báo các phần phụ thuộc cho những thuộc tính cần tính toán.

- Cú pháp template của Vue khai thác toàn bộ sức mạnh của các biểu thức JavaScript, trong khi các cú pháp và biểu thức của Handlebars khá là hạn chế.

- Về hiệu suất, Vue vượt qua Ember [với khoảng cách đáng kể](https://rawgit.com/krausest/js-framework-benchmark/master/webdriver-ts/table.html), thậm chí là sau khi engine mới nhất Glimmer cập nhật trên Ember 2.x. Những bản cập nhật của Vue được tự động nâng cấp, trong khi với Ember bạn cần phải chạy bằng lặp bằng tay trong những tình huống nặng về hiệu suất.

## Knockout

Knockout đã từng là một tiên phong trong MVVM và theo dấu không gian phụ thuộc và hệ thống tương tác của nó thì rất tương đồng với Vue. Việc [hỗ trợ trình duyệt](http://knockoutjs.com/documentation/browser-support.html) cũng vô cùng ấn tượng với mọi thứ Knockout làm đều hỗ trợ tới IE6! Vue ngược lại chỉ hỗ trợ IE9+.

Qua thời gian, sự phát triển của Knockout đã chậm lại và nó bắt đầu thể hiện một chút sự lỗi thời. Ví dụ, hệ thống component của nó thiếu một tập hợp đầy đủ các móc vào vòng đời của component và cho dù trong các tình huống sử dụng phổ biến, giao diện để truyền con vào một component cảm giác một chút vụng về khi so sánh với [Vue](components.html#Content-Distribution-with-Slots).

Cũng có một vài khác biệt về triết lý trong thiết kế API mà nếu bạn tò mò, bạn có thể xem mô phỏng cách mà mỗi framework xử lý việc tạo một [danh sách việc làm đơn giản](https://gist.github.com/chrisvfritz/9e5f2d6826af00fcbace7be8f6dccb89)
Nó rõ ràng có vẻ hơi chủ quan, nhưng nhiều người cho rằng API của Vue thì ít phức tạp và cấu trúc tốt hơn.

## Polymer

Polymer là một project được Google tài trợ và thực tế cũng là một nguồn cảm hứng cho Vue. Component của Vue có thể khá giống với 'custom element' của Polymer và cả 2 cùng cung cấp một phong cách phát triển tương tự nhau. Sự khác nhau lớn nhất là Polymer được xây dựng dựa trên tính năng mới nhất của Web Componets và yêu cầu những polyfill () quan trọng để hoạt động (với hiệu năng giảm) trên những trình duyệt không hỗ trợ mặc định những tính năng đó. Ngược lại, Vue hoạt động mà không cần bất cứ điểu kiện tiên quyết hay polyfill xuống IE9.

Trong Polymer 1.0, đội phát triển Polymer đã làm việc hệ thống kết nối data rất giới hạn để bù lại được tốc độ. Ví dụ, những biểu thức được hỗ trợ bởi Polymer template là biểu thức logic và những lời gọi đơn hàm. Những cài đặt được tính toán cũng rất hạn chế.

Những custom element của Polymer được viết trong các file HTML, chúng giới hạn bạn với JavaScript và CSS thuần (và những ngôn ngữ tính năng được hỗ trợ bởi các trình duyệt hiện nay). Trong khi đó, các component đơn file của Vue cho phép bạn có thể dễ dàng sử dụng ES2015+ và bất cứ trình tiền xử lý CSS nào mà bạn muốn.

Khi chạy một sản phẩm, Polymer khuyến khích tải mọi thứ on-the-fly() với HTML Imports, với việc giả sử rằng các trình duyệt đều được tích hợp spec và hỗ trợ HTTP/2 ở cả server và client. Việc này là có thể hoặc không thể phụ thuộc vào đối tượng người dùng và môi trường mà ứng dụng được chạy. Trong trường hợp mà việc này không khả thi, bạn sẽ phải sử dụng một công cụ đặc biệt gọi là Vulcanizer để đóng gói các element Polymer của bạn. Trong lĩnh vực này, Vue có thể kết hợp tính năng component bất đồng bộ của nó với tính năng code-splitting của webpack để dễ dàng chia các phần của ứng dụng để đóng gói và lazy-loaded. Việc này đảm bảo chắc chắn tính tương thích với những trình duyệt cũ hơn trong khi vẫn giữ được hiệu suất tải ứng dụng tuyệt vời.

Nó hoàn toàn là có thể để cung cấp một sự tích hợp sâu hơn giữa Vue và Web Component ví dụ như Custom Elements và Shadow DOM đóng gói các style - tuy nhiên vào thời điểm hiện tại, chúng tôi vẫn đang chờ cho những tính năng đó được hoàn thiện và được cài đặt rộng rãi ở tất cả các trình duyệt phổ biến trước khi tạo bất cứ sự cam kết nghiêm túc với chúng.

## Riot

Riot 2.0 cung cấp một mô hình phát triển dựa trên component (component-based) tương tự (được gọi là "tag" trong Riot), với một hệ thống API được thiết kế tối giản và "đẹp". Riot and Vue có vẻ chia sẻ rất nhiều trong triết lý thiết kế. Tuy nhiên, mặc dù nặng hơn Riot một chút, Vue thực sự cung cấp một số những lợi thế đáng kế:

- [Hệ thống hiệu ứng chuyển đổi](transitions.html). Riot không có.
- Một hệ thống điều hướng (router) mạnh mẽ hơn nhiều. Router API (API điều hướng) của Riot vô cùng tối giản.
- Hiệu xuất tốt hơn. Riot sử dụng việc [duyệt qua một cây DOM](http://riotjs.com/compare/#virtual-dom-vs-expressions-binding) thay vì sử dụng một DOM ảo (virtual DOM) khiến nó phải chịu các vấn đề về hiệu xuất giống như AngularJS.
- Hỗ trợ công các công cụ hoàn thiện hơn. Vue cung cấp sự hỗ trợ chính thức cho [webpack](https://github.com/vuejs/vue-loader) và [Browserify](https://github.com/vuejs/vueify), trong khi đó Riot phải dựa vào dự hộ trợ của cộng đồng cho hệ thống xây dựng tích hợp.
