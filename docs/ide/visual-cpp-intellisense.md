---
title: C++ IntelliSense
description: C++ projenizi kodlarken kullanabileceğiniz bazı IntelliSense özellikleri hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 10/08/2018
ms.topic: conceptual
author: corob-msft
ms.author: corob
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: 53ef15fda9ac09fc7d38ed2b6bbcfe8605ac8d5d
ms.sourcegitcommit: 7a300823cf1bd3355be03bde561cf2777bc09eae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2021
ms.locfileid: "133977490"
---
# <a name="visual-c-intellisense-features"></a>Visual C++ IntelliSense özellikleri

IntelliSense, kodlamayı daha kolay hale getirmek için bir özellik kümesine verilen addır. C++ için IntelliSense, tek başına dosyalar ve bir C++ projesinin parçası olan dosyalar için de kullanılabilir. Platformlar arası projelerde, bazı IntelliSense özellikleri, bir Android veya iOS bağlamında olsanız bile, paylaşılan kod projesindeki *. cpp* ve *. c* dosyalarında kullanılabilir.

Bu makalede C++ IntelliSense özelliklerine genel bakış sunulmaktadır. Projenizi IntelliSense için yapılandırma ve sorunları giderme hakkında daha fazla bilgi için bkz. [IntelliSense Için C++ projesi yapılandırma](visual-cpp-intellisense-configuration.md).

## <a name="intellisense-features-in-c"></a>C++ ' da IntelliSense özellikleri

IntelliSense, kodlamayı daha kolay hale getirmek için bir özellik kümesine verilen addır. Farklı kişilerin ne kullanışlı olduğuna ilişkin farklı fikirleri olduğundan, IntelliSense özelliklerinin neredeyse hepsi, **metin düzenleyici**   >  **C/C++**  >  **Gelişmiş** altında Seçenekler iletişim kutusunda etkinleştirilebilir veya devre dışı bırakılabilir. **Seçenekler** iletişim kutusu, menü çubuğundaki **Araçlar** menüsünden kullanılabilir.

![Araç seçenekleri iletişim kutusu](../ide/media/sintellisensecpptoolsoptions.PNG)

IntelliSense 'e erişmek için aşağıdaki görüntüde gösterilen menü öğelerini ve klavye kısayollarını kullanabilirsiniz.

![IntelliSense menüsü](../ide/media/vs2015_cpp_intellisense_menu.png)

## <a name="statement-completion-and-member-list"></a>Ekstre tamamlama ve üye listesi

Bir anahtar sözcük, tür, işlev, değişken adı veya derleyicinin tanıdığı diğer program öğesini yazmaya başladığınızda, düzenleyici sizin için sözcüğü tamamlamayı önerir.

Simgelerin ve anlamlarıyla ilgili bir liste için, bkz. [sınıf görünümü ve nesne tarayıcısı simgeleri](../ide/class-view-and-object-browser-icons.md).

![Visual C&#43;&#43; Tamam Word penceresi](../ide/media/vs2015_cpp_complete_word.png)

Üye listesini ilk kez çağırdığınızda, yalnızca geçerli bağlam için erişilebilen üyeleri gösterir. Bundan sonra **CTRL** + **J** tuşlarına basarsanız, erişilebilirliğinden bağımsız olarak tüm üyeleri gösterir. Üçüncü kez çağırırsanız, daha geniş bir program öğeleri listesi gösterilir. **Seçenekler** iletişim kutusundaki üye listesini, **metin düzenleyici**  >  **C/C++**  >  **genel**  >  **otomatik liste üyeleri** altında devre dışı bırakabilirsiniz.

![Visual C&#43;&#43; üye listesi](../ide/media/vs2015_cpp_list_members.png)

## <a name="parameter-help"></a>Parametre yardımı

Bir işlev çağrısının açma ayracı veya bir sınıf şablonu değişken bildiriminde açılı ayraç yazdığınızda, düzenleyici, işlevin veya oluşturucunun her bir aşırı yüklemesiyle ilgili parametre türleriyle küçük bir pencere gösterir. &mdash;İmleç konumunu temel alan "geçerli" parametresi &mdash; kalın yazılmıştır. **Seçenekler** iletişim kutusundaki parametre bilgilerini **metin düzenleyici**  >  **C/C++**  >  **genel**  >  **parametre bilgileri** altında devre dışı bırakabilirsiniz.

![Visual C&#43;&#43; parametresi yardımı](../ide/media/vs_2015_cpp_param_help.png)

## <a name="quick-info"></a>Hızlı Bilgi

Fare imlecini bir değişken üzerine getirdiğinizde, tür bilgilerini ve türün tanımlandığı üstbilgiyi gösteren küçük bir pencere satır içi görüntülenir. İşlevin imzasını görmek için bir işlev çağrısının üzerine gelin. **Seçenekler** iletişim kutusunda, **metin düzenleyici**  >  **C/C++**  >  **Gelişmiş**  >  **otomatik hızlı bilgi**' nin altındaki hızlı bilgileri devre dışı bırakabilirsiniz.

![Visual C&#43;&#43; QuickInfo](../ide/media/vs2015_cpp_quickinfo.png)

## <a name="error-squiggles"></a>Hata dalgalı çizgiler

Dalgalı çizgiler bir program öğesi (değişken, anahtar sözcük, küme ayracı, tür adı vb.) altında bir hata veya koddaki olası bir hataya dikkat edin. Bir iletme bildirimi yazdığınızda, uygulamayı yazmanız gerektiğini hatırlatmak için yeşil bir dalgalı çizgi görünür. şu anda etkin olmayan kodda bir hata olduğunda, örneğin, Windows bağlamda çalışırken, ancak Android bağlamında hata olabilecek bir değer girdiğinizde, bir paylaşılan projede mor dalgalı çizgi görünür. Kırmızı dalgalı çizgi, bir derleyici hatasını veya bir uyarı ile uğraşmanız gereken etkin kodda uyarı olduğunu gösterir.

![Visual C&#43;&#43; hatası dalgalı çizgiler](../ide/media/vs2015_cpp_error_quiggles.png)

### <a name="code-colorization-and-fonts"></a>Kod renklendirme ve yazı tipleri

Varsayılan renkler ve yazı tipleri,  **ortam**  >  **yazı tipleri ve renkler** altında Seçenekler iletişim kutusunda değiştirilebilir. Yalnızca düzenleyiciden değil, burada birçok UI penceresi için yazı tiplerini değiştirebilirsiniz. C++ ' a özel ayarlar "C++" ile başlar; diğer ayarlar tüm diller içindir.

## <a name="cross-platform-intellisense"></a>Platformlar arası IntelliSense

Paylaşılan bir kod projesinde, Android bağlamında çalışırken bile dalgalı çizgiler gibi bazı IntelliSense özellikleri kullanılabilir. Etkin olmayan bir projede hataya neden olacak bir kod yazarsanız, IntelliSense hala dalgalı çizgiler gösterir, ancak geçerli bağlamdaki hatalar için dalgalı çizgiler 'den farklı bir renkte yer alırlar.

Android ve iOS için derlemek üzere yapılandırılmış bir OpenGLES uygulaması düşünün. Çizim, düzenlenmekte olan paylaşılan kodu gösterir. Bu görüntüde, etkin proje **iOS. StaticLibrary**'dir:

![etkin proje olarak iOS seçilidir.](../ide/media/intellisensecppcrossplatform2.png)

Aşağıdakilere dikkat edin:

- `#ifdef` `__ANDROID__` İOS projesi için tanımlanmadığı için, 6. satırdaki dal, etkin olmayan bir bölgeyi gösterecek şekilde gri renkte olur.

- 11. satırdaki tebrik değişkeni `HELLO` , artık kırmızı renkli bir çizgi olan tanımlayıcıyla başlatılır. Bunun nedeni `HELLO` Şu anda etkin olan iOS projesinde tanımlayıcı tanımlanmamıştır.

- `BYE`Bu tanımlayıcı (Şu anda) etkin olmayan **Android. NativeActivity** projesinde tanımlanmadığı için, 12. satırda, tanımlayıcı üzerinde mor bir çizgi vardır. Bu satır iOS etkin proje olduğunda derlense de, Android etkin proje olduğunda derlenmez. Bu paylaşılan kod olduğundan, geçerli etkin yapılandırmada derlense de kodu düzeltmeniz gerekir.

Etkin projeyi Android olarak değiştirirseniz dalgalı çizgiler değişikliği:

- `#else` `__ANDROID__` Android projesi için tanımlandığından, 8. satırdaki dal, etkin olmayan bir bölgeyi gösterecek şekilde gri renkte.

- 11. satırdaki tebrik değişkeni `HELLO` , mor renkli bir çizgi olan tanımlayıcıyla başlatılır. Bunun nedeni `HELLO` Şu anda etkin olmayan iOS projesinde tanımlayıcı tanımlanmamıştır.

- Bu tanımlayıcı etkin projede tanımlanmadığı için, bu tanımlayıcı üzerinde kırmızı renkli bir dalgalı çizgi vardır `BYE` .

## <a name="intellisense-for-stand-alone-files"></a>Tek başına dosyalar için IntelliSense

Herhangi bir projenin dışında tek bir dosya açtığınızda IntelliSense 'i yine de kullanmaya devam edersiniz. **Seçenekler** iletişim kutusunda belirli IntelliSense özelliklerini, **metin düzenleyici**  >  **C/C++**  >  **Gelişmiş** altında etkinleştirebilir veya devre dışı bırakabilirsiniz. IntelliSense 'i bir projenin parçası olmayan tek dosyalar için yapılandırmak üzere, **proje dışı dosyalar Için IntelliSense ve gözatma** bölümüne bakın.

![Visual C&#43;&#43; tek dosya IntelliSense](../ide/media/vs2015_cpp_single_file_intellisense.png)

Varsayılan olarak, tek dosya IntelliSense yalnızca üst bilgi dosyalarını bulmak için standart içerme dizinlerini kullanır. Daha fazla dizin eklemek için, **çözüm** düğümündeki kısayol menüsünü açın ve aşağıdaki çizimde gösterildiği gibi, dizini **hata ayıklama kaynak kodu** listesine ekleyin:

![Üst bilgi dosyasına bir yol ekleniyor.](../ide/media/intellisensedebugyourcode.jpg)

## <a name="enable-or-disable-features"></a>Özellikleri etkinleştirme veya devre dışı bırakma

Farklı kişilerin ne kullanışlı olduğuna ilişkin farklı fikirleri olduğundan, IntelliSense özelliklerinin neredeyse hepsi, **metin düzenleyici**   >  **C/C++**  >  **Gelişmiş** altında Seçenekler iletişim kutusunda etkinleştirilebilir veya devre dışı bırakılabilir. **Seçenekler** iletişim kutusu, menü çubuğundaki **Araçlar** menüsünden kullanılabilir.

![Araç seçenekleri iletişim kutusu](../ide/media/sintellisensecpptoolsoptions.PNG)

## <a name="see-also"></a>Ayrıca bkz.

- [IntelliSense kullanma](../ide/using-intellisense.md)
- [IntelliSense için bir C++ projesi yapılandırma](visual-cpp-intellisense-configuration.md)
