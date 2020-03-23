---
title: C++ IntelliSense
ms.date: 10/08/2018
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: c0d1be12f733a858bf223fb1dce6a091c0dc6c50
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75594220"
---
# <a name="visual-c-intellisense-features"></a>Visual C++ IntelliSense özellikleri

IntelliSense, kodlamayı daha kullanışlı hale getiren bir dizi özelliğe verilen bir addır. IntelliSense for C++ tek başına dosyaların yanı sıra C++ projesinin bir parçası olan dosyalar için de kullanılabilir. Platformlar arası projelerde, Android veya iOS bağlamında olsanız bile paylaşılan kod projesinde *.cpp* ve *.c* dosyalarında bazı IntelliSense özellikleri bulunur.

Bu makalede, C++ IntelliSense özelliklerine genel bir bakış sağk. Projenizi IntelliSense için nasıl yapılandırılabildiğiniz ve sorunları nasıl gidereceğiniz hakkında bilgi için Bkz. [IntelliSense için bir C++ projesini yapılandırma.](visual-cpp-intellisense-configuration.md)

## <a name="intellisense-features-in-c"></a>C++'da IntelliSense özellikleri

IntelliSense, kodlamayı daha kullanışlı hale getiren bir dizi özelliğe verilen bir addır. Farklı kişilerin neyin uygun olduğu konusunda farklı fikirleri olduğundan, IntelliSense özelliklerinin hemen hemen tümü, **Text Editor** > **C/C++** > **Advanced**altında **Seçenekler** iletişim kutusunda etkinleştirilebilir veya devre dışı tutulabilir. **Seçenekler** iletişim kutusu, menü çubuğundaki **Araçlar** menüsünden kullanılabilir.

![Araç Seçenekleri iletişim kutusu](../ide/media/sintellisensecpptoolsoptions.PNG)

IntelliSense'e erişmek için aşağıdaki resimde gösterilen menü öğelerini ve klavye kısayollarını kullanabilirsiniz.

![IntelliSense menüsü](../ide/media/vs2015_cpp_intellisense_menu.png)

## <a name="statement-completion-and-member-list"></a>Ekstre tamamlama ve üye listesi

Derleyicinin tanıdığı bir anahtar kelime, tür, işlev, değişken adı veya başka bir program öğesi yazmaya başladığınızda, düzenleyici sözcüğü sizin için tamamlamayı teklif eder.

Simgelerin ve anlamlarının listesi için [Sınıf Görünümü ve Nesne Tarayıcı simgelerine](../ide/class-view-and-object-browser-icons.md)bakın.

![Görsel C&#43;&#43; Word'&#43;&#43; Tamamla penceresi](../ide/media/vs2015_cpp_complete_word.png)

Üye listesini ilk kez çağırdığınızda, yalnızca geçerli bağlam için erişilebilir olan üyeleri gösterir. Bundan sonra **Ctrl**+**J** tuşuna baslarsanız, erişilebilirlik ne olursa olsun tüm üyeleri gösterir. Üçüncü kez çağırırsanız, program öğelerinin daha da geniş bir listesi gösterilir. **Text Editor** > **C/C++** > **Genel** > **Otomatik liste üyeleri**altında **Seçenekler** iletişim kutusundaki üye listesini kapatabilirsiniz.

![Visual C&#43;&#43; Üye Listesi](../ide/media/vs2015_cpp_list_members.png)

## <a name="parameter-help"></a>Parametre yardımı

Bir işlev çağrısının açılış ayraçını veya sınıf şablonu değişken bildirimine açı ayracı yazdığınızda, düzenleyici işlevin veya oluşturucunun her yükü için parametre türlerine sahip küçük bir pencere gösterir. İmleç konumuna&mdash;&mdash;dayalı "geçerli" parametresi kalın renktedir. **Metin**  > **Düzenleyicisi C/C++** > **Genel** > **Parametre bilgileri**altında Seçenekler iletişim kutusundaki parametre bilgilerini kapatabilirsiniz. **Text Editor**

![Görsel C&#43;&#43; Parametre Yardımı](../ide/media/vs_2015_cpp_param_help.png)

## <a name="quick-info"></a>Hızlı Bilgi

Fare imlecini bir değişkenin üzerine gonttunuzda, tür bilgilerini ve türün tanımlandığı üstbilgiyi gösteren küçük bir pencere satır içinde görünür. İşlevin imzasını görmek için bir işlev çağrısının üzerine titreyin. Metin > **Düzenleyicisi C/C++** > **Advanced** > Auto **Text Editor****Quick Info** **altında, Seçenekler** iletişim kutusunda Hızlı Bilgi'yi kapatabilirsiniz.

![Visual C&#43;&#43; QuickInfo](../ide/media/vs2015_cpp_quickinfo.png)

## <a name="error-squiggles"></a>Hata squiggles

Bir program öğesi (değişken, anahtar kelime, ayraç, tür adı vb.) altında dalgalanır, dikkatinizi koddaki bir hataya veya olası hataya çeker. Uygulamayı hala yazmanız gerektiğini hatırlatmak için bir ileri bildirimi yazdığınızda yeşil bir kıvrım belirir. Paylaşılan bir projede, örneğin Windows bağlamında çalışırken ancak Android bağlamında hata olacak bir şey girdiğinizde, şu anda etkin olmayan bir kod hatası olduğunda mor bir dalgalı belirir. Kırmızı dalgalı bir derleyici hata veya uyarı ile uğraşmak gerekir etkin kod gösterir.

![Görsel C&#43;&#43; hata squiggles](../ide/media/vs2015_cpp_error_quiggles.png)

### <a name="code-colorization-and-fonts"></a>Kod renklendirme ve yazı tipleri

Varsayılan renkler ve yazı **tipleri,** **Çevre** > **Yazı Tipleri ve Renkler**altında Seçenekler iletişim kutusunda değiştirilebilir. Burada birçok UI penceresi için yazı tiplerini değiştirebilirsiniz, sadece düzenleyici değil. C++'a özgü ayarlar "C++" ile başlar; diğer ayarlar tüm diller içindir.

## <a name="cross-platform-intellisense"></a>Platform ötesi IntelliSense

Paylaşılan bir kod projesinde, Android bağlamında çalışırken bile squiggles gibi bazı IntelliSense özellikleri kullanılabilir. Etkin olmayan bir projede hataya neden olacak bazı kodlar yazarsanız, IntelliSense hala dalgalı bir şekilde gösterir, ancak bunlar geçerli bağlamdaki hatalar için squiggles'dan farklı bir renktedir.

Android ve iOS için yapılandırılacak bir OpenGLES Uygulamasını düşünün. Resimde paylaşılan kod düzenleniyor. Bu resimde, etkin proje **iOS.StaticLibrary**:

![iOS etkin proje olarak seçilir.](../ide/media/intellisensecppcrossplatform2.png)

Aşağıdakilere dikkat edin:

- iOS projesi için `#ifdef` `__ANDROID__` tanımlanmadığından, satır 6'daki dal etkin olmayan bir bölgeyi belirtmek için gri renkte dir.

- Satır 11'deki karşılama `HELLO`değişkeni, şimdi kırmızı bir dalgalı olan tanımlayıcı ile başharfe işlenir. Bunun nedeni, şu anda `HELLO` etkin olan iOS projesinde tanımlayıcı nın tanımlanmamış olmasıdır.

- Bu tanımlayıcı (şu anda) etkin olmayan `BYE` **Android.NativeActivity** projesinde tanımlanmadığından Satır 12'de tanımlayıcıda mor bir dalgalı lık vardır. Ios etkin proje olduğunda bu satır derlese de, Android etkin proje olduğunda derlemeolmaz. Bu paylaşılan kod olduğundan, şu anda etkin yapılandırmada derlenmiş olsa bile kodu düzeltmeniz gerekir.

Etkin projeyi Android olarak değiştirirseniz, dalgalı geçişler:

- `#else` Android projesi için tanımlandığı için, 8. `__ANDROID__`

- Satır 11'deki karşılama değişkeni, mor bir `HELLO`dalgalı olan tanımlayıcı ile başharfe işlenir. Bunun nedeni, `HELLO` şu anda etkin olmayan iOS projesinde tanımlayıcı nın tanımlanmamış olmasıdır.

- Bu tanımlayıcı etkin projede tanımlanmadığından Satır 12'nin tanımlayıcısında `BYE` kırmızı bir dalgalı lık vardır.

## <a name="intellisense-for-stand-alone-files"></a>Bağımsız dosyalar için IntelliSense

Herhangi bir projenin dışında tek bir dosyayı açtığınızda, yine de IntelliSense olsun. **Text Editor** > **C/C++** > **Advanced** **altında, Seçenekler** iletişim kutusunda belirli IntelliSense özelliklerini etkinleştirebilir veya devre dışı kullanabilirsiniz. Projenin parçası olmayan tek dosyalar için IntelliSense'i yapılandırmak **için IntelliSense'i arayın ve proje dışı dosyalar bölümüne göz atın.**

![Görsel C&#43;&#43; tek dosya intellisense](../ide/media/vs2015_cpp_single_file_intellisense.png)

Varsayılan olarak, tek dosya IntelliSense yalnızca üstbilgi dosyalarını bulmak için standart dahil dizinleri kullanır. Ek dizinler eklemek **için, Çözüm** düğümündeki kısayol menüsünü açın ve aşağıdaki çizimde gösterildiği gibi dizininizi **Hata Ayıklama Kaynak Kodu** listesine ekleyin:

![Üstbilgi dosyasına yol ekleme.](../ide/media/intellisensedebugyourcode.jpg)

## <a name="enable-or-disable-features"></a>Özellikleri etkinleştirme veya devre dışı

Farklı kişilerin neyin uygun olduğu konusunda farklı fikirleri olduğundan, IntelliSense özelliklerinin hemen hemen tümü, **Text Editor** > **C/C++** > **Advanced**altında **Seçenekler** iletişim kutusunda etkinleştirilebilir veya devre dışı tutulabilir. **Seçenekler** iletişim kutusu, menü çubuğundaki **Araçlar** menüsünden kullanılabilir.

![Araç Seçenekleri iletişim kutusu](../ide/media/sintellisensecpptoolsoptions.PNG)

## <a name="see-also"></a>Ayrıca bkz.

- [IntelliSense Kullanma](../ide/using-intellisense.md)
- [IntelliSense için bir C++ projesi yapılandırma](visual-cpp-intellisense-configuration.md)
