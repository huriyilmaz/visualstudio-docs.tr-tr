---
title: JavaScript IntelliSense | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense [JavaScript]
- <reference> JavaScript XML tag
- JavaScript Code Editor
- XML code comments, JavaScript IntelliSense
- reference JavaScript XML tag
- JavaScript, IntelliSense
- code comments, JavaScript IntelliSense
- JavaScript, reference groups
- JavaScript Editor
- reference directives [JavaScript]
- JavaScript, XML documentation comments
- reference groups [JavaScript]
- JavaScript, reference directives
- IntelliSense [JavaScript], about
- IntelliSense extensibility [JavaScript]
- XML documentation comments [JavaScript]
ms.assetid: af1a3171-c9d8-45a3-9c96-a763e3b163ef
caps.latest.revision: 67
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 39c90a8550736c945f04467e9366a73039cfa2b1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670472"
---
# <a name="javascript-intellisense"></a>JavaScript IntelliSense
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

IntelliSense, kodu oluşturduğunuz sırada size bilgi sağlayarak daha hızlı ve daha az hatayla kod yazmanıza yardımcı olur. JavaScript Düzenleyicisi'nde istemci komut dosyasıyla çalıştığınız sırada, IntelliSense geçerli bağlamınızı temel alarak uygun nesneleri, işlevleri, özellikleri ve parametreleri listeler. IntelliSense'in sağladığı açılan listeden bir kodlama seçeneğini belirleyerek kodunuzu tamamlayabilirsiniz.

 IntelliSense aşağıdaki görevleri tamamlamayı kolaylaştırır:

- Üye bilgilerini bulun.

- Dil öğelerini doğrudan kodunuza ekleyin.

- Kod düzenleyicisinden çıkmak zorunda kalmadan bağlamınızı koruyun.

- XML belgeleri yorumları ve JavaScript IntelliSense genişletilebilirlik özelliği ile özel IntelliSense'i destekleyin.

  Bu konu aşağıdaki bölümleri içermektedir:

- [IntelliSense bağlamını belirleme](#DeterminingIntelliSenseContext)

- [IntelliSense bilgilerini işleme](#ProcessingIntelliSenseInformation)

- [JavaScript IntelliSense özellikleri](#Features)

- [JavaScript IntelliSense genişletilebilirliği](#Extensibility)

- [JavaScript doğrulaması](#Validation)

  @No__t_0 IntelliSense işlevselliği hakkında daha fazla bilgi için bkz. [IntelliSense kullanma](../ide/using-intellisense.md).

## <a name="DeterminingIntelliSenseContext"></a>IntelliSense bağlamını belirleme
 JavaScript IntelliSense, geçerli komut dosyası bağlamınızla alakalı tüm komut dosyalarını temel alarak kodlama seçenekleri sağlar. Geçerli dosyadaki betik oluşturma öğeleri de buna dahildir. Ayrıca, komut dosyası başvuruları, derleme komut dosyası başvuruları, hizmet başvuruları ve sayfayla ilişkili başvurular gibi, komut dosyanızın doğrudan ya da dolaylı olarak başvurduğu her kodu içerir.

 Geçerli komut dosyası bağlamınız aşağıdaki öğeler temel alınarak oluşturulur:

- Etkin belgedeki tüm komut dosyası bloklarında tanımlı işlevler. Dosya adı uzantısı .aspx., .ascx, .master, .html ve .htm olan dosyalarda satır içi komut dosyası blokları desteklenir.

- başka bir betik dosyasına işaret eden `src` öznitelikleri olan öğeleri `script`. Hedef komut dosyasının dosya adı uzantısı .js olmalıdır.

- @No__t_0 yönergesini kullanarak diğer JavaScript dosyalarına başvuran JavaScript dosyaları.

- Genel nesneler, IntelliSense uzantıları veya gecikmeli yüklenen komut dosyaları için başvuru grupları.

- XML Web hizmetlerine yapılan başvurular.

- @No__t_0 ve <xref:System.Web.UI.ScriptManagerProxy> denetimleri, Web uygulaması AJAX özellikli bir ASP.NET uygulamasıdır.

- @No__t_0, AJAX etkinleştirilmiş bir ASP.NET Web uygulamasında çalışıyorsanız.

    > [!NOTE]
    > IntelliSense, HTML öğelerinde olay işleyicisi özniteliklerinde olan veya `href` özniteliklerde tanımlanmış komut dosyası için desteklenmez.

## <a name="ProcessingIntelliSenseInformation"></a>IntelliSense bilgilerini işleme
 JavaScript IntelliSense sağlamak için dil hizmeti aşağıdaki işlemleri gerçekleştirir:

- Etkin belgedeki başvuruları temel alan ve başvurulan dosyalardaki özyinelemeli inceleme komut dosyası başvurularını temel alan bağımlı JavaScript dosyalarının bir listesini oluşturur.

- Listeyi dikkatle inceler ve her bir dosyadan tür bilgilerini ve diğer ilgili verileri toplar.

- Verileri bir araya toplar ve JavaScript dil servisine aktarır; böylece tür bilgileri ve veriler IntelliSense'in kullanımına sunulur.

- Dosyaları, IntelliSense listesini etkileyebilecek değişiklikler açısından izler ve gerektiğinde listeyi güncelleştirir. Uzak depolardaki (HTTP kullanılarak başvurulan depolar gibi) komut dosyaları izlenmez.

## <a name="Features"></a>JavaScript IntelliSense özellikleri
 JavaScript IntelliSense aşağıdaki nesneleri destekler:

- [Belge Nesne Modeli (DOM) öğeleri](#HTMLDom)

- [İç nesneler](#IntrinsicObjects)

- [Kullanıcı tanımlı değişkenler, işlevler ve nesneler](#UserDefined)

- Dış dosyalarda [komut dosyası başvuruları](#Script), [başvuru yönergeleri](#ReferenceDirectives)ve [başvuru grupları](#ReferenceGroups)gibi başvurular kullanılarak tanımlanan nesneler.

- Uzak dosyalarda tanımlı olup Visual Studio tarafından indirilen nesneler.

- [XML belgeleri yorumlarında](#XMLDocComments)belirtilen parametreler ve alanlar gibi nesneler.

- Standart JavaScript açıklama etiketleri (//) kullanılarak açıklanan nesneler. Daha fazla bilgi için bkz. [JavaScript IntelliSense 'ı genişletme](../ide/extending-javascript-intellisense.md).

- [JavaScript IntelliSense genişletilebilirlik](#Extensibility) mekanizması kullanılarak desteklenen nesneler. Daha fazla bilgi için bkz. [JavaScript IntelliSense 'ı genişletme](../ide/extending-javascript-intellisense.md).

- [ASP.NET AJAX nesneleri](#ASPNet)

  IntelliSense bir nesnenin türünü belirleyemediğinde, etkin belgedeki tanımlayıcıları kullanarak deyim tamamlama seçenekleri sunar. Daha fazla bilgi için bkz. [tanımlayıcılar Için deyimin tamamlanması](../ide/statement-completion-for-identifiers.md).

### <a name="HTMLDom"></a>HTML DOM öğeleri
 JavaScript IntelliSense, `body`, `form` ve `div` gibi dinamik HTML (DHTML) DOM öğeleri için programlama başvuruları sağlar. IntelliSense yalnızca, geçerli belgede ve ana sayfada yer alan öğeleri görüntüler. JavaScript IntelliSense Ayrıca `window` ve `document` nesnelerini ve üyelerini destekler.

### <a name="IntrinsicObjects"></a>İç nesneler
 JavaScript IntelliSense, `Array`, `String`, `Math`, `Date` ve `Number` gibi iç nesneler için programlama başvuruları sağlar. İç nesneler hakkında daha fazla bilgi için bkz. [Standart yerleşik nesneler](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects).

### <a name="UserDefined"></a>Kullanıcı tanımlı değişkenler, Işlevler ve nesneler
 Bir JavaScript dosyasını değiştirdiğinizde, [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] tüm kullanılabilir kod kaynaklarını belirleyebilmek için, açılan ve başvurulan belgeleri tarar. Bu, oluşturduğunuz değişkenleri, işlevleri ve nesneleri içerir. Bu kaynaklar daha sonra JavaScript IntelliSense kullanımına sunulur.

 Kullanıcı tanımlı değişkenler, işlevler ve nesneler hakkında daha fazla bilgi için MSDN Web sitesinde [kendi nesnelerinizi oluşturma](http://go.microsoft.com/fwlink/?LinkId=108671) konusuna bakın.

### <a name="External"></a>Dış dosya başvuruları
 Kodunuzda IntelliSense desteği elde etmek için çeşitli türlerde harici dosya başvuruları ekleyebilirsiniz. Harici dosya başvuruları; komut dosyası başvuruları ve başvuru yönergeleri olabileceği gibi, başvuru grupları kullanılarak da belirtilebilir.

#### <a name="Script"></a>Betik başvuruları
 Tüm istemci komut dosyasını bir sayfaya yazmak yerine, komut dosyası kodu içeren harici dosyalara başvuruda bulunabilirsiniz. Böylece, kodu sayfalar arasında yeniden kullanmanız daha kolay olur ve istemci komut dosyasının tarayıcı tarafından önbelleğe alınmasına olanak sağlanır.

 ASP.NET AJAX özellikli bir Web sayfasıyla çalışmıyorsanız, bir `script` öğesinin açılış etiketindeki `src` özniteliğini kullanarak bir dış betik dosyasına başvurabilirsiniz. @No__t_0 özniteliği, kaynak kodu veya verileri içeren bir dış dosyanın URL 'sini belirtir.

 Aşağıdaki örnekte, bir komut dosyasına başvurmak için bir < `script` > etiketinde `src` özniteliğini kullanan biçimlendirme gösterilmektedir.

```html
<script type="text/javascript" src="~/Scripts/JavaScript.js">

</script>
```

 ASP.NET AJAX özellikli bir Web sayfasıyla çalışıyorsanız, <xref:System.Web.UI.ScriptManager> denetiminin <xref:System.Web.UI.ScriptReference> nesnesini kullanarak betik dosyalarına başvurabilirsiniz.

 Aşağıdaki örnek, bir komut dosyasına başvurmak için bir <xref:System.Web.UI.ScriptManager> denetimindeki <xref:System.Web.UI.ScriptReference> nesnesini kullanan biçimlendirmeyi gösterir.

```html
<asp:ScriptManager ID="ScriptManager1" runat="server">
  <Scripts>
    <asp:ScriptReference Path="~/Scripts/JavaScript.js" />
  </Scripts>
</asp:ScriptManager>
```

 IntelliSense, ASP.NET AJAX Web uygulamalarında bir derlemeye kaynak olarak eklenen komut dosyalarını da destekler. Katıştırılmış betik kaynakları hakkında daha fazla bilgi için bkz. [Izlenecek yol: bir JavaScript dosyasını bir derlemede kaynak olarak katıştırma](https://msdn.microsoft.com/library/d8cb78cd-95a9-4dc6-92df-391866817e89).

#### <a name="ReferenceDirectives"></a>Başvuru yönergeleri
 @No__t_0 yönergesi [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)], düzenlemekte olduğunuz betiği ve diğer betikleri arasında bir ilişki kurmasını sağlar. @No__t_0 yönergesi, geçerli betik dosyasının komut dosyası bağlamına bir betik dosyası eklemenizi sağlar. Böylece, kodunuzu yazarken IntelliSense'in harici olarak tanımlı işlevlere, türlere ve alanlara başvuruda bulunabilmesi sağlanır.

 Bir `reference` yönergesini bir XML yorumu biçiminde oluşturursunuz. Bu yönerge, dosya içinde tüm diğer komut dosyalarından önce bildirilmelidir. @No__t_0 yönergesi, disk tabanlı betik başvurusu, derleme tabanlı betik başvurusu, hizmet tabanlı betik başvurusu veya sayfa tabanlı betik başvurusu içerebilir.

 Aşağıdaki örnekte, disk tabanlı başvuru yönergelerinin kullanımına dair örnekler gösterilmektedir. İlk örnekte, dil servisi, proje dosyasını (örneğin, .jsproj) içeren aynı klasörde ilgili dosyayı da arar.

 `/// <reference path="ScriptFile1.js" />`

 `/// <reference path="Scripts/ScriptFile2.js" />`

 `/// <reference path="../ScriptFile3.js" />`

 `/// <reference path="~/Scripts/ScriptFile4.js" />`

 Aşağıdaki örnekte, derleme tabanlı bir komut dosyası için nasıl başvuru oluşturulacağı gösterilmektedir.

 `/// <reference name "Ajax.js" assembly="System.Web.Extensions, ..." />`

 Aşağıdaki örnekte, hizmet tabanlı komut dosyasına nasıl başvurulacağı gösterilmektedir:

 `/// <reference path="MyService.asmx" />`

 `/// <reference path="Services/MyService.asmx" />`

 `/// <reference path="../MyService.asmx" />`

 `/// <reference path="~/Services/MyService.asmx" />`

> [!NOTE]
> Web Uygulama Projeleri'nde (WAP), Web hizmeti (.asmx) dosyaları içinde yer alan komut dosyası için JavaScript IntelliSense desteklenmez.

 Aşağıdaki örnekte, sayfa tabanlı komut dosyasına nasıl başvurulacağı gösterilmektedir:

 `/// <reference path="Default.aspx" />`

 `/// <reference path="Admin/Default.aspx" />`

 `/// <reference path="../Default.aspx" />`

 `/// <reference path="~/Admin/Default.aspx" />`

 Aşağıdaki kurallar `reference` yönergesi için geçerlidir.

- @No__t_0 XML yorumu herhangi bir komut dosyasından önce bildirilmelidir.

- XML açıklamaları sözdizimini üç eğik çizgi ile kullanmalısınız. Standart açıklamalar sözdizimi (iki eğik çizgi) kullanılarak yapılan başvurular yoksayılır.

- Yönerge başına yalnızca tek bir dosya veya kaynak belirtilebilir.

- Sayfa tabanlı komut dosyalarına yönelik birden fazla başvuruya izin verilmez.

- Bir sayfa başvurusu belirtiliyorsa, başka hiçbir türde başvuru yönergesine izin verilmez.

- Dosya adlarında göreli yollar kullanılır. Uygulama köküne göreli yollar yapmak için, tilde işlecini (`~`) kullanabilirsiniz.

- Mutlak yollar yoksayılır.

- Başvurulan sayfalardaki başvuru yönergeleri işlenmez; yani başvuru yönergeleri sayfalar için özyinelemeli olarak çözümlenmez. Yalnızca sayfanın doğrudan başvurduğu komut dosyası dahil edilir.

#### <a name="ReferenceGroups"></a>Başvuru grupları
 Belirli IntelliSense .js dosyalarının farklı JavaScript projeleri için kapsamda olduğunu belirtmek için önceden tanımlı başvuru gruplarını kullanabilirsiniz. Aşağıdaki başvuru grubu türleri kullanılabilir:

- JavaScript kullanan [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] uygulamalar için örtük (Windows). Bu grupta yer alan dosyalar, belirtilen türdeki proje için Kod Düzenleyicisi'nde açılan her .js dosyası için kapsama girer.

- Örtük (Web); HTML5 projeleri için. Bu grupta yer alan dosyalar, bu proje türleri için Kod Düzenleyicisi'nde açılan her .js dosyası için kapsama girer.

- Adanmış çalışan başvuru grupları; HTML5 Web Çalışanları için. Bu grupta belirtilen dosyalar, bir adanmış çalışan başvuru grubuna dair açık başvuru içeren .js dosyaları için kapsama girer.

- Genel; diğer JavaScript proje türleri için.

  Çoğu senaryoda başvuru gruplarını değiştirmeniz gerekmez. Ancak, değişiklikler yapmak istiyorsanız, başvuru gruplarında yer alan dosyaları belirtmek için JavaScript Kodu Düzenleyicisi'ne ilişkin yapılandırma seçeneklerini kullanabilirsiniz. Bu özelliği kullanma hakkında yönergeler için bkz. [Seçenekler, metin düzenleyici, JavaScript, IntelliSense](../ide/reference/options-text-editor-javascript-intellisense.md).

> [!TIP]
> IntelliSense başvuruları genellikle genel nesneler ve IntelliSense [uzantıları](#Extensibility)için IntelliSense desteği sağlamak üzere kullanılır. Bu seçeneği ayrıca, komut dosyası yükleyici kullanılarak çalışma zamanında yüklenmesi gereken komut dosyaları için de kullanabilirsiniz.

### <a name="remote-file-references"></a>Uzak Dosya Başvuruları
 Uzak bir dosya veya kitaplık için IntelliSense desteği sağlamak amacıyla, Visual Studio'ya bir JavaScript dosyasında başvurulan uzak JavaScript dosyalarını indirme talimatı verebilirsiniz. Bu özelliği kullandığınızda, JavaScript dosyanıza bir başvuru olarak eklediğiniz dosyalar indirilir.

> [!NOTE]
> Web projeleri dışında, bu özelik yalnızca projenin bağlamı dışında açılan JavaScript dosyaları için çalışır. Web projeleri için, projenizde başvurulan uzak dosyalar varsayılan olarak indirilir.

 Bu özelliği kullanma hakkında yönergeler için bkz. [Seçenekler, metin düzenleyici, JavaScript, IntelliSense](../ide/reference/options-text-editor-javascript-intellisense.md).

> [!WARNING]
> Bu özelliği etkinleştirir ve Kod Düzenleyicisi'nde daha yavaş bir performans gözlemlerseniz, özelliği devre dışı bırakmanızı öneririz.

### <a name="XMLDocComments"></a>XML belge açıklamaları
 XML belgeleri yorumları, komut dosyasına eklediğiniz kod öğelerinin metin açıklamalarıdır. Bu metin açıklamaları IntelliSense'te, yorumda bulunulan komut dosyasına başvurduğunuz zamanlarda görüntülenir. Örneğin, bir işlevin parametreleri ve dönüş değeri hakkında bilgi verebilirsiniz. XML belgeleri yorumlarına yalnızca dosyalardan, derlemelerden ve hizmetlerden ulaşılabilir. Daha fazla bilgi için bkz. [XML belge açıklamaları](../ide/xml-documentation-comments-javascript.md) ve [XML belgesi açıklamaları oluşturma](../ide/create-xml-documentation-comments-for-javascript-intellisense.md).

 IntelliSense XML belgeleri yorumlarını şu senaryolarda görüntüleyebilir:

- Başka bir .js dosyasına başvuruda bulunan .js dosyası.

- Bir .aspx dosyasına başvuruda bulunan .js dosyası.

- Bir .js dosyasına başvuruda bulunan .aspx dosyası.

  Bir .aspx dosyası başka bir .aspx dosyasına başvurduğunda IntelliSense kullanılamaz.

### <a name="ASPNet"></a>ASP.NET AJAX nesneleri
 ASP.NET AJAX da JavaScript IntelliSense'i destekler. ASP.NET AJAX, ECMAScript (JavaScript) içinde kullanılabilen standart türlerin kapsamını genişleten bir istemci çerçevesi içerir. JavaScript IntelliSense 'i ASP.NET AJAX nesneleriyle ilgili ayrıntıları sağlamak üzere etkinleştirmek için, [!INCLUDE[atlaslib_current_ext](../includes/atlaslib-current-ext-md.md)] tamamında XML belge açıklamaları eklenmiştir. ASP.NET AJAX Kitaplığı'nda yer alan türleri ve üyeleri kullandığınızda bu XML belgeleri yorumları görüntülenir.

> [!NOTE]
> Özel üyeler JavaScript IntelliSense tarafından görüntülenmez. Özel üyeler, ASP.NET AJAX içinde, bir alt çizgi (_) ile başlayan üyeler olarak belirtilir.

## <a name="Extensibility"></a>JavaScript IntelliSense genişletilebilirliği
 JavaScript dil servisi, üçüncü taraf kitaplıkları kullanan geliştiriciler için IntelliSense deneyimini değiştirmenize olanak sağlayan nesneleri ve işlevleri sunar. Özellikle de varsayılan dil servisinin müşterilere vermek istediğiniz tüm bilgileri sağlayamadığı durumlarda bu özellikler yararlı olur. Daha fazla bilgi için bkz. [JavaScript IntelliSense 'ı genişletme](../ide/extending-javascript-intellisense.md).

## <a name="Validation"></a>JavaScript doğrulaması
 JavaScript komut dosyası doğrulaması arka planda sürekli gerçekleşir. @No__t_0 JavaScript kodunda sözdizimi hataları algıladığında, aşağıdaki yollarla geri bildirim sağlanır:

- Düzenleyicide altı çizili öğeler. Dalgalı kırmızı alt çizgiler hataları gösterir. Fare işaretçisini hatanın üzerinde tutarsanız, bir araç ipucu hata açıklamasını görüntüler.

- **Hata listesi** pencere. **Hata listesi** penceresinde hata açıklaması, hatanın oluştuğu dosya, satır ve sütun numarası ve proje gösterilir. **Hata listesi** penceresini görüntülemek Için, **Görünüm** menüsünde **hata listesi**' a tıklayın.

- Çıkış penceresi yüklenmemiş başvuruları gösterir.

## <a name="see-also"></a>Ayrıca Bkz.
- [IntelliSense Kullanma](../ide/using-intellisense.md)
- [XML Belge Açıklamaları Oluşturma](../ide/create-xml-documentation-comments-for-javascript-intellisense.md)
- [JavaScript IntelliSense Genişletme](../ide/extending-javascript-intellisense.md)
- [Tanımlayıcılar İçin İfade Tamamlama](../ide/statement-completion-for-identifiers.md)
- [XML Belge Açıklamaları](../ide/xml-documentation-comments-javascript.md)
- [DHTML nesne modeli hakkında](http://go.microsoft.com/fwlink/?LinkID=92344)
- [Üyeleri Listele](https://msdn.microsoft.com/1b9cc469-9cd4-4d42-9999-1f9479635ff8)
- [SRC özniteliği &#124; src özelliği](http://go.microsoft.com/fwlink/?LinkId=92345)