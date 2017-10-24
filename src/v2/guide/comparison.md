---
title: So sánh với những framework khác
type: guide
order: 801
---

Đây chắc chắc là trang khó nhất để viết trong toàn bộ phần hướng dẫn này, nhưng chúng tôi cảm thấy nó quan trọng. Có điều chắc chắn là, bạn có các vấn đề bạn đã cố gắng giải quyết và sử dụng một thư viện khác để làm việc đó. Bạn ở đây bởi vì bạn muốn biết xem Vue có thể giải quyết chúng tốt hơn không. Và đó là cái mà chúng tôi hi vọng sẽ cho bạn câu trả lời.

Chúng tôi cũng rất cố gắng để tránh thiên vị. Là những thành viên chính, chúng tôi chắc chắc thích Vue rất nhiều. Có những vấn đề chúng tôi nghĩ Vue giải quyết tốt hơn bất cứ thư viên nào khác. Nếu chúng tôi không tin tưởng vào điều đó, chúng tôi sẽ không tiếp tục xây dụng Vue. Mặc dù vậy, chúng tôi cũng muốn sự công bằng và chính xác. Khi những thư viện khác cung cấp những lợi ích đáng kể, ví dụ như hệ sinh thái đồ sộ các renderer thay thế của React hay việc Knockout hỗ trợ trình duyệt tới tận IE6, chúng tôi cũng cố gắng liệt kê chúng.

Chúng tôi cũng muốn **các bạn** giúp cho tài liệu này được cập nhật bởi vì "thế giới" JavaScript phát triển rất nhanh! Nếu bạn nhận ra một sự thiếu chính xác hoặc một cái gì đó có vẻ không đúng, vui lòng cho chúng tôi biết bằng việc [mở một issue](https://github.com/vuejs/vuejs.org/issues/new?title=Inaccuracy+in+comparisons+guide).

## React

React và Vue chia sẻ nhiều điểm tương đồng. Cả 2 đều:

- sử dụng một virtual DOM()
- provide reactive and composable view components
-
- Tập trung duy trì phần lõi của thư viện, với những tính năng ví dụ như routing(điều hướng) và quản lý trạng thái toàn cục được giải quyết bằng các thư viện hỗ trợ

Being so similar in scope, we've put more time into fine-tuning this comparison than any other. We want to ensure not only technical accuracy, but also balance. We point out where React outshines Vue, for example in the richness of their ecosystem and abundance of their custom renderers.

With that said, it's inevitable that the comparison would appear biased towards Vue to some React users, as many of the subjects explored are to some extent subjective. We acknowledge the existence of varying technical taste, and this comparison primarily aims to outline the reasons why Vue could potentially be a better fit if your preferences happen to coincide with ours.

The React community [has been instrumental](https://github.com/vuejs/vuejs.org/issues/364) in helping us achieve this balance, with special thanks to Dan Abramov from the React team. He was extremely generous with his time and considerable expertise to help us refine this document until we were [both happy](https://github.com/vuejs/vuejs.org/issues/364#issuecomment-244575740) with the final result.

### Hiệu suất

Both React and Vue offer comparable performance in most commonly seen use cases, with Vue usually slightly ahead due to its lighter-weight Virtual DOM implementation. If you are interested in numbers, you can check out this [3rd party benchmark](https://rawgit.com/krausest/js-framework-benchmark/master/webdriver-ts/table.html) which focuses on raw rendering/updating performance. Note that this does not take complex component structures into account, so should only be considered a reference rather than a verdict.

Cả React và Vue đều cung cấp một hiệu suất khá tương đồng trong hầu hết các tình huống sử dụng, và Vue thường nhanh hơn một chút nhờ vào việc cài đặt được một Virtual DOM nhẹ hơn. Nếu bạn có hứng thú với các con số thì [3rd party benchmark](https://rawgit.com/krausest/js-framework-benchmark/master/webdriver-ts/table.html) cung cấp số liệu hiệu suất tập trung vào raw rendering/updating. Lưu ý rằng số liệu kia không tính đến các trường hợp cấu trúc component phức tạp, do đó các bạn chỉ nên lấy nó để tham khảo chứ nó không phải đánh giá chính thức về hiệu suất.

#### Optimization Efforts

In React, when a component's state changes, it triggers the re-render of the entire component sub-tree, starting at that component as root. To avoid unnecessary re-renders of child components, you need to either use `PureComponent` or implement `shouldComponentUpdate` whenever you can. You may also need to use immutable data structures to make your state changes more optimization-friendly. However, in certain cases you may not be able to rely on such optimizations because `PureComponent/shouldComponentUpdate` assumes the entire sub tree's render output is determined by the props of the current component. If that is not the case, then such optimizations may lead to inconsistent DOM state.

Trong React, khi state của một component thay đổi, nó sẽ render lại toàn bộ component phụ, bắt đầu từ component đó như là gốc. Để tránh việc render lại component con một cách không cần thiết, bạn hoặc là phải sử dụng `PureComponent` hoặc cài đặt `shouldComponentUpdate` khi có thể. Bạn có thể cũng cần phải sử dụng cấu trúc dữ liệu không thay đổi để làm cho việc thay đổi state dễ dàng tối ưu. Tuy nhiên, trong những trường hợp cụ thể, bạn không thể nào tin tưởng vào

In Vue, a component's dependencies are automatically tracked during its render, so the system knows precisely which components actually need to re-render when state changes. Each component can be considered to have `shouldComponentUpdate` automatically implemented for you, without the nested component caveats.

Trong Vue, những dependencies của một component được tự động theo dõi khi nó được render, nhờ đó hệ thống biết chính xác component nào thực sự cần được render lại khi có thay đổi về trạng thái. Mỗi component có thể được hiểu là tự động có `shouldComponentUpdate` được cài đặt sẵn cho bạn mà không

Overall this removes the need for a whole class of performance optimizations from the developer's plate, and allows them to focus more on building the app itself as it scales.

### HTML & CSS

In React, everything is just JavaScript. Not only are HTML structures expressed via JSX, the recent trends also tend to put CSS management inside JavaScript as well. This approach has its own benefits, but also comes with various trade-offs that may not seem worthwhile for every developer.

Trong React, tất cả mọi thứ đều là JavaScript. Không những cấu trúc HTML được biểu diễn qua JSX, mà một số xu hướng gần đây đưa phần quản lý CSS vào bên trong JavaScript nữa. Cách tiếp cận này có những lợi ích của nó, nhưng đồng thời cũng phải trả giá mà có vẻ là không đáng cho tất cả mọi nhà phát triển.

Vue embraces classic web technologies and builds on top of them. To show you what that means, we'll dive into some examples.

Vue

#### JSX với Templates

In React, all components express their UI within render functions using JSX, a declarative XML-like syntax that works within JavaScript.

Trong React, tất cả component biểu diễn giao diện với các render function sử dụng JSX, một kiểu cú pháp khai báo giống như XML mà tương thích với JavaScript.

Render functions with JSX have a few advantages:
Các function render với JSX có một số lợi ích:

- You can leverage the power of a full programming language (JavaScript) to build your view. This includes temporary variables, flow controls, and directly referencing JavaScript values in scope.

- The tooling support (e.g. linting, type checking, editor autocompletion) for JSX is in some ways more advanced than what's currently available for Vue templates.

In Vue, we also have [render functions](render-function.html) and even [support JSX](render-function.html#JSX), because sometimes you do need that power. However, as the default experience we offer templates as a simpler alternative. Any valid HTML is also a valid Vue template, and this leads to a few advantages of its own:

Trong Vue, chúng tôi cũng có các [render function](render-function.html) và thậm chí [hỗ trợ JSX](render-function.html#JSX), bởi vì thỉnh thoảng bạn cần khả năng đó. Tuy nhiên, trải nghiệm mặc định chúng tôi cung cấp template như là một sự thay thế đơn giản hơn. Bất cứ cú pháp html hợp lệ nào cũng hợp lệ trong Vue template, việc này mang đến một số những lợi ích của nó:

- For many developers who have been working with HTML, templates feel more natural to read and write. The preference itself can be somewhat subjective, but if it makes the developer more productive then the benefit is objective.

- Với nhiều nhà phát triển, những người đã và đang làm việc với HTML, template cho cảm giác tự nhiên hơn để đọc và viết. Lợi thế này bản thân nó có vẻ hơi chủ quan, nhưng nếu nó giúp cho lập trình viên hiệu quả hơn thì lợi ích của nó là khách quan.

-  HTML-based templates make it much easier to progressively migrate existing applications to take advantage of Vue's reactivity features.

- Những template dựa trên HTML giúp cho nó dễ dàng hơn để chuyển những ứng dụng có sẵn sang Vue với những lợi thế về tương tác.

- It also makes it much easier for designers and less experienced developers to parse and contribute to the codebase.

- Việc này cũng làm dễ dàng hơn cho người thiết kế và những lập trình viên ít kinh nghiệm có thể chuyển đổi và đóng góp vào trong codebase.

- You can even use pre-processors such as Pug (formerly known as Jade) to author your Vue templates.

- Bạn thậm chí có thể sử dụng những bộ biên tập trước (pre-processors) như Pug (trước đây được biết đến với tên Jade) để tạo Vue template của bạn.

Some argue that you'd need to learn an extra DSL (Domain-Specific Language) to be able to write templates - we believe this difference is superficial at best. First, JSX doesn't mean the user doesn't need to learn anything - it's additional syntax on top of plain JavaScript, so it can be easy for someone familiar with JavaScript to learn, but saying it's essentially free is misleading. Similarly, a template is just additional syntax on top of plain HTML and thus has very low learning cost for those who are already familiar with HTML. With the DSL we are also able to help the user get more done with less code (e.g. `v-on` modifiers). The same task can involve a lot more code when using plain JSX or render functions.

Một số người cho rằng bạn cần phải học thêm DSL(Domain-Specific Language - Ngôn ngữ cụ thể miền)

On a higher level, we can divide components into two categories: presentational ones and logical ones. We recommend using templates for presentational components and render function / JSX for logical ones. The percentage of these components depends on the type of app you are building, but in general we find presentational ones to be much more common.

Ở một cấp cao hơn, chúng ta có thể chia component thành 2 loại:

#### Component-Scoped CSS

Unless you spread components out over multiple files (for example with [CSS Modules](https://github.com/gajus/react-css-modules)), scoping CSS in React is often done via CSS-in-JS solutions (e.g. [styled-components](https://github.com/styled-components/styled-components), [glamorous](https://github.com/paypal/glamorous), and [emotion](https://github.com/emotion-js/emotion)). This introduces a new component-oriented styling paradigm that is different from the normal CSS authoring process. Additionally, although there is support for extracting CSS into a single stylesheet at build time, it is still common that a runtime will need to be included in the bundle for styling to work properly. While you gain access to the dynamism of JavaScript while constructing your styles, the tradeoff is often increased bundle size and runtime cost.

If you are a fan of CSS-in-JS, many of the popular CSS-in-JS libraries support Vue (e.g. [styled-components-vue](https://github.com/styled-components/vue-styled-components) and [vue-emotion](https://github.com/egoist/vue-emotion)). The main difference between React and Vue here is that the default method of styling in Vue is through more familiar `style` tags in [single-file components](single-file-components.html).


Nếu bạn là một fan của CSS-in-JS, có nhiều thư viện CSS-in-JS hỗ trợ Vue (ví dụ: [styled-components-vue](https://github.com/styled-components/vue-styled-components) và [vue-emotion](https://github.com/egoist/vue-emotion)). Khác biệt lớn nhất giữa React và Vue ở đây là phương pháp style mặc định của Vue giống với `style` tag trong [single-file-components](single-file-components.html)

[Single-file components](single-file-components.html) give you full access to CSS in the same file as the rest of your component code.
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

The optional `scoped` attribute automatically scopes this CSS to your component by adding a unique attribute (such as `data-v-21e5b78`) to elements and compiling `.list-container:hover` to something like `.list-container[data-v-21e5b78]:hover`.

Thuộc tính tùy chọn `scoped` sẽ tự động giới hạn CSS này chỉ trong component của bạn bằng việc thêm một thuộc tính duy nhất (ví dụ như `data-v-21e5b78`) vào và dịch `list-containter:hover` thành kiểu như `.list-containter[data-v-21e5b78]:hover`

Lastly, the styling in Vue's single-file component's is very flexible. Through [vue-loader](https://github.com/vuejs/vue-loader), you can use any preprocessor, post-processor, and even deep integration with [CSS Modules](https://vue-loader.vuejs.org/en/features/css-modules.html) -- all within the `<style>` element.

Cuối cùng, styling trong một file (single-file) của Vue rất linh hoạt. Thông qua [vue-loader](https://github.com/vuejs/vue-loader), bạn có thể sử dụng bất cứ một trình dịch trước(preprocessor), dịch sau(post-processor), và thậm chí có thể tích hợp sâu với [CSS Modules](https://vue-loader.vuejs.org/en/features/css-modules.html) -- tất cả chỉ với `<style>`.

### Scale

#### Scaling Up

For large applications, both Vue and React offer robust routing solutions. The React community has also been very innovative in terms of state management solutions (e.g. Flux/Redux). These state management patterns and [even Redux itself](https://github.com/egoist/revue) can be easily integrated into Vue applications. In fact, Vue has even taken this model a step further with [Vuex](https://github.com/vuejs/vuex), an Elm-inspired state management solution that integrates deeply into Vue that we think offers a superior development experience.

Another important difference between these offerings is that Vue's companion libraries for state management and routing (among [other concerns](https://github.com/vuejs)) are all officially supported and kept up-to-date with the core library. React instead chooses to leave these concerns to the community, creating a more fragmented ecosystem. Being more popular though, React's ecosystem is considerably richer than Vue's.

Finally, Vue offers a [CLI project generator](https://github.com/vuejs/vue-cli) that makes it trivially easy to start a new project using your choice of build system, including [webpack](https://github.com/vuejs-templates/webpack), [Browserify](https://github.com/vuejs-templates/browserify), or even [no build system](https://github.com/vuejs-templates/simple). React is also making strides in this area with [create-react-app](https://github.com/facebookincubator/create-react-app), but it currently has a few limitations:

- It does not allow any configuration during project generation, while Vue's project templates allow [Yeoman](http://yeoman.io/)-like customization.
- It only offers a single template that assumes you're building a single-page application, while Vue offers a wide variety of templates for various purposes and build systems.
- It cannot generate projects from user-built templates, which can be especially useful for enterprise environments with pre-established conventions.

It's important to note that many of these limitations are intentional design decisions made by the create-react-app team and they do have their advantages. For example, as long as your project's needs are very simple and you never need to "eject" to customize your build process, you'll be able to update it as a dependency. You can read more about the [differing philosophy here](https://github.com/facebookincubator/create-react-app#philosophy).

#### Scaling Down

React is renowned for its steep learning curve. Before you can really get started, you need to know about JSX and probably ES2015+, since many examples use React's class syntax. You also have to learn about build systems, because although you could technically use Babel Standalone to live-compile your code in the browser, it's absolutely not suitable for production.

While Vue scales up just as well as, if not better than React, it also scales down just as well as jQuery. That's right - all you have to do is drop a single script tag into a page:

``` html
<script src="https://cdn.jsdelivr.net/npm/vue"></script>
```

Then you can start writing Vue code and even ship the minified version to production without feeling guilty or having to worry about performance problems.

Since you don't need to know about JSX, ES2015, or build systems to get started with Vue, it also typically takes developers less than a day reading [the guide](./) to learn enough to build non-trivial applications.

### Native Rendering

React Native enables you to write native-rendered apps for iOS and Android using the same React component model. This is great in that as a developer, you can apply your knowledge of a framework across multiple platforms. On this front, Vue has an official collaboration with [Weex](https://alibaba.github.io/weex/), a cross-platform UI framework developed by Alibaba Group, which uses Vue as its JavaScript framework runtime. This means with Weex, you can use the same Vue component syntax to author components that can not only be rendered in the browser, but also natively on iOS and Android!

At this moment, Weex is still in active development and is not as mature and battle-tested as React Native, but its development is driven by the production needs of the largest e-commerce business in the world, and the Vue team will also actively collaborate with the Weex team to ensure a smooth experience for Vue developers.

Another option Vue developers will soon have is [NativeScript](https://www.nativescript.org/), via a [community-driven plugin](https://github.com/rigor789/nativescript-vue).

### With MobX

MobX has become quite popular in the React community and it actually uses a nearly identical reactivity system to Vue. To a limited extent, the React + MobX workflow can be thought of as a more verbose Vue, so if you're using that combination and are enjoying it, jumping into Vue is probably the next logical step.

## AngularJS (Angular 1)

Some of Vue's syntax will look very similar to AngularJS (e.g. `v-if` vs `ng-if`). This is because there were a lot of things that AngularJS got right and these were an inspiration for Vue very early in its development. There are also many pains that come with AngularJS however, where Vue has attempted to offer a significant improvement.

Một vài cú pháp của Vue trông sẽ rất giống với AngularJS (ví dụ: `v-if` với `ng-if`). Bởi vì AngularJS có rất nhiều thứ đúng đắn đã là nguồn cảm hứng cho Vue trong những ngày đầu phát triển. Tuy nhiên cũng có rất nhiều những hạn chế của AngularJS mà Vue cố gắng cải thiện một cách

### Độ phức tạp

Vue is much simpler than AngularJS, both in terms of API and design. Learning enough to build non-trivial applications typically takes less than a day, which is not true for AngularJS.

Vue thì đơn giản hơn AngularJS, bao gồm cả API và thiết kế. Thời gian học đủ để xây dựng một ứng dụng không vớ vẩn thường chỉ mất ít hơn một ngày, với AngularJS thì không thể.

### Flexibility and Modularity

AngularJS has strong opinions about how your applications should be structured, while Vue is a more flexible, modular solution. While this makes Vue more adaptable to a wide variety of projects, we also recognize that sometimes it's useful to have some decisions made for you, so that you can just start coding.

That's why we offer a [webpack template](https://github.com/vuejs-templates/webpack) that can set you up within minutes, while also granting you access to advanced features such as hot module reloading, linting, CSS extraction, and much more.

### Data binding

AngularJS uses two-way binding between scopes, while Vue enforces a one-way data flow between components. This makes the flow of data easier to reason about in non-trivial applications.

### Directives vs Components

Vue has a clearer separation between directives and components. Directives are meant to encapsulate DOM manipulations only, while components are self-contained units that have their own view and data logic. In AngularJS, there's a lot of confusion between the two.

### Performance

Vue has better performance and is much, much easier to optimize because it doesn't use dirty checking. AngularJS becomes slow when there are a lot of watchers, because every time anything in the scope changes, all these watchers need to be re-evaluated again. Also, the digest cycle may have to run multiple times to "stabilize" if some watcher triggers another update. AngularJS users often have to resort to esoteric techniques to get around the digest cycle, and in some situations, there's no way to optimize a scope with many watchers.

Vue doesn't suffer from this at all because it uses a transparent dependency-tracking observation system with async queueing - all changes trigger independently unless they have explicit dependency relationships.

Interestingly, there are quite a few similarities in how Angular and Vue are addressing these AngularJS issues.

## Angular (Từng được biết đến là Angular 2)

We have a separate section for the new Angular because it really is a completely different framework from AngularJS. For example, it features a first-class component system, many implementation details have been completely rewritten, and the API has also changed quite drastically.

Chúng tôi có một phần riêng dành cho Angular mới bởi vì nó thực sự là một framework mới hoàn toàn so với AngularJS. Ví dụ,

### TypeScript

Angular essentially requires using TypeScript, given that almost all its documentation and learning resources are TypeScript-based. TypeScript has its benefits - static type checking can be very useful for large-scale applications, and can be a big productivity boost for developers with backgrounds in Java and C#.

Angular về cơ bản yêu cầu sử dụng TypeScript, bằng chứng là hầu hết tất cả tài liệu hướng dẫn và học tập đều dựa trên TypeScript. TypeScript có cho mình những lợi ích - kiểm tra kiểu tĩnh sẽ rất có ích cho những ứng dụng quy mô lớn, và có thể làm tăng hiệu quả làm việc cho những developer có nền tảng với Java và C#.

However, not everyone wants to use TypeScript. In many smaller-scale use cases, introducing a type system may result in more overhead than productivity gain. In those cases you'd be better off going with Vue instead, since using Angular without TypeScript can be challenging.

Tuy nhiên, không phải tất cả mọi người đều muốn sử dụng TypeScript. Trong nhiều trường hợp những ứng dụng nhỏ, việc có một hệ thống kiểu có thể gấy rối trí nhiều hơn là hiệu quả. Trong những trường hợp đó, bạn tốt nhất nên dùng Vue, bởi vì sử dụng Angular mà không có TypeScript có thể khá thử thách.

Finally, although not as deeply integrated with TypeScript as Angular is, Vue also offers [official typings](https://github.com/vuejs/vue/tree/dev/types) and [official decorator](https://github.com/vuejs/vue-class-component) for those who wish to use TypeScript with Vue. We are also actively collaborating with the TypeScript and VSCode teams at Microsoft to improve the TS/IDE experience for Vue + TS users.

Cuối cùng, mặc dù không tích hợp sâu với TypeScript như Angular, Vue cũng cung cấp [các kiểu chính thức](https://github.com/vuejs/vue/tree/dev/types) và [decorator chính thức](https://github.com/vuejs/vue-class-component) cho những ai ước rằng có thể sử dụng TypeScript với Vue. Chúng tôi cũng tích cực hợp tác với nhóm làm TypeScript và VSCode của Microsoft để nâng cao trải nghiệm của TS/IDE cho Vue và người dùng TypeScript.

### Kích thước và hiệu suát

In terms of performance, both frameworks are exceptionally fast and there isn't enough data from real world use cases to make a verdict. However if you are determined to see some numbers, Vue 2.0 seems to be ahead of Angular according to this [3rd party benchmark](http://stefankrause.net/js-frameworks-benchmark4/webdriver-ts/table.html).

Nhắc đến hiệu suất, cả 2 framework đều rất nhanh và không có đủ dữ liệu từ thực tế để có thể xác định. Tuy nhiên, nếu các bạn muốn thấy một vài con số, Vue 2.0 dường như đang dẫn trước so với Angular theo như [3rd party benchmark](http://stefankrause.net/js-frameworks-benchmark4/webdriver-ts/table.html).

Recent versions of Angular, with [AOT compilation](https://en.wikipedia.org/wiki/Ahead-of-time_compilation) and [tree-shaking](https://en.wikipedia.org/wiki/Tree_shaking), have been able to get its size down considerably. However, a full-featured Vue 2 project with Vuex + Vue Router included (~30KB gzipped) is still significantly lighter than an out-of-the-box, AOT-compiled application generated by `angular-cli` (~130KB gzipped).

Các phiên bản gần đây của Angular, với [AOT compilation](https://en.wikipedia.org/wiki/Ahead-of-time_compilation) và [tree-shaking](https://en.wikipedia.org/wiki/Tree_shaking), giúp cho kích thước của Angular giảm đáng kể. Tuy nhiên, một dự án đầy đủ tính năng của Vue 2 với Vuex + Vue Router (~30KB gzipped) vẫn nhẹ hơn nhiều so với một ứng dụng AOT-compiled được sinh tự động bởi `angular-cli` (~130KB gzipped).

### Độ linh hoạt

Vue is much less opinionated than Angular, offering official support for a variety of build systems, with no restrictions on how you structure your application. Many developers enjoy this freedom, while some prefer having only one Right Way to build any application.

Vue ít cứng nhắc hơn nhiều so với Angular, với việc hỗ trợ chính thức cho nhiều hệ xây dựng khác nhau và không có một giới hạn nào trong việc bạn cấu trúc ứng dụng của mình. Nhiều nhà phát triển thích sự tự do này, trong khi những người khác thì thích chỉ có duy nhất một cách đúng để xây dựng ứng dụng.

### Lộ trình học tập

To get started with Vue, all you need is familiarity with HTML and ES5 JavaScript (i.e. plain JavaScript). With these basic skills, you can start building non-trivial applications within less than a day of reading [the guide](./).

Để bắt đầu với Vue, tất cả những gì bạn cần là quen thuộc với HTML và ES5 JavaScript (ví dụ: JavaScript thuần). Với những kĩ năng cơ bản này, bạn có thể bắt đầu xây dựng một ứng dụng hẳn hỏi với ít hơn một ngày ngồi đọc [hướng dẫn](./).

Angular's learning curve is much steeper. The API surface of the framework is huge and as a user you will need to familiarize yourself with a lot more concepts before getting productive. The complexity of Angular is largely due to its design goal of targeting only large, complex applications - but that does make the framework a lot more difficult for less-experienced developers to pick up.


## Ember

Ember is a full-featured framework that is designed to be highly opinionated. It provides a lot of established conventions and once you are familiar enough with them, it can make you very productive. However, it also means the learning curve is high and flexibility suffers. It's a trade-off when you try to pick between an opinionated framework and a library with a loosely coupled set of tools that work together. The latter gives you more freedom but also requires you to make more architectural decisions.

That said, it would probably make a better comparison between Vue core and Ember's [templating](https://guides.emberjs.com/v2.10.0/templates/handlebars-basics/) and [object model](https://guides.emberjs.com/v2.10.0/object-model/) layers:

- Vue provides unobtrusive reactivity on plain JavaScript objects and fully automatic computed properties. In Ember, you need to wrap everything in Ember Objects and manually declare dependencies for computed properties.

- Vue's template syntax harnesses the full power of JavaScript expressions, while Handlebars' expression and helper syntax is intentionally quite limited in comparison.

- Performance-wise, Vue outperforms Ember [by a fair margin](https://rawgit.com/krausest/js-framework-benchmark/master/webdriver-ts/table.html), even after the latest Glimmer engine update in Ember 2.x. Vue automatically batches updates, while in Ember you need to manually manage run loops in performance-critical situations.

## Knockout

Knockout was a pioneer in the MVVM and dependency tracking spaces and its reactivity system is very similar to Vue's. Its [browser support](http://knockoutjs.com/documentation/browser-support.html) is also very impressive considering everything it does, with support back to IE6! Vue on the other hand only supports IE9+.

Over time though, Knockout development has slowed and it's begun to show its age a little. For example, its component system lacks a full set of lifecycle hooks and although it's a very common use case, the interface for passing children to a component feels a little clunky compared to [Vue's](components.html#Content-Distribution-with-Slots).

There also seem to be philosophical differences in the API design which if you're curious, can be demonstrated by how each handles the creation of a [simple todo list](https://gist.github.com/chrisvfritz/9e5f2d6826af00fcbace7be8f6dccb89). It's definitely somewhat subjective, but many consider Vue's API to be less complex and better structured.

## Polymer

Polymer is yet another Google-sponsored project and in fact was a source of inspiration for Vue as well. Vue's components can be loosely compared to Polymer's custom elements and both provide a very similar development style. The biggest difference is that Polymer is built upon the latest Web Components features and requires non-trivial polyfills to work (with degraded performance) in browsers that don't support those features natively. In contrast, Vue works without any dependencies or polyfills down to IE9.

Polymer là một project được Google tài trợ và thực tế cũng là một nguồn cảm hứng cho Vue. Component của Vue có thể khá giống với 'custom element' của Polymer và cả 2 cùng cung cấp một phong cách phát triển tương tự nhau. Sự khác nhau lớn nhất là Polymer

In Polymer 1.0, the team has also made its data-binding system very limited in order to compensate for the performance. For example, the only expressions supported in Polymer templates are boolean negation and single method calls. Its computed property implementation is also not very flexible.

Trong Polymer 1.0, đội phát triển

Polymer custom elements are authored in HTML files, which limits you to plain JavaScript/CSS (and language features supported by today's browsers). In comparison, Vue's single file components allows you to easily use ES2015+ and any CSS preprocessors you want.

When deploying to production, Polymer recommends loading everything on-the-fly with HTML Imports, which assumes browsers implementing the spec, and HTTP/2 support on both server and client. This may or may not be feasible depending on your target audience and deployment environment. In cases where this is not desirable, you will have to use a special tool called Vulcanizer to bundle your Polymer elements. On this front, Vue can combine its async component feature with webpack's code-splitting feature to easily split out parts of the application bundle to be lazy-loaded. This ensures compatibility with older browsers while retaining great app loading performance.

Khi chạy một sản phẩm, Polymer khuyến khích tải mọi thứ on-the-fly()

It is also totally feasible to offer deeper integration between Vue with Web Component specs such as Custom Elements and Shadow DOM style encapsulation - however at this moment we are still waiting for the specs to mature and be widely implemented in all mainstream browsers before making any serious commitments.



## Riot

Riot 2.0 cung cấp một mô hình phát triển dựa trên component (component-based) tương tự (được gọi là "tag" trong Riot), với một hệ thống API được thiết kế tối giản và "đẹp". Riot and Vue có vẻ chia sẻ rất nhiều trong triết lý thiết kế. Tuy nhiên, mặc dù nặng hơn Riot một chút, Vue thực sự cung cấp một số những lợi thế đáng kế:

- [Hệ thống hiệu ứng chuyển đổi](transitions.html). Riot không có.
- Một hệ thống điều hướng (router) mạnh mẽ hơn nhiều. Router API (API điều hướng) của Riot vô cùng tối giản.
- Hiệu xuất tốt hơn. Riot sử dụng việc [duyệt qua một cây DOM](http://riotjs.com/compare/#virtual-dom-vs-expressions-binding) thay vì sử dụng một DOM ảo (virtual DOM) khiến nó phải chịu các vấn đề về hiệu xuất giống như AngularJS.
- Hỗ trợ công các công cụ hoàn thiện hơn. Vue cung cấp sự hỗ trợ chính thức cho [webpack](https://github.com/vuejs/vue-loader) và [Browserify](https://github.com/vuejs/vueify), trong khi đó Riot phải dựa vào dự hộ trợ của cộng đồng cho hệ thống xây dựng tích hợp.
