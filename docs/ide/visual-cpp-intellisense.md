---
title: C++IntelliSense
ms.date: 10/08/2018
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: c0d1be12f733a858bf223fb1dce6a091c0dc6c50
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75594220"
---
# <a name="visual-c-intellisense-features"></a>Visual C++ IntelliSense özellikleri

IntelliSense, kodlamayı daha kolay hale getirmek için bir özellik kümesine verilen addır. İçin C++ IntelliSense, tek başına dosyalar ve C++ projenin parçası olan dosyalar için de kullanılabilir. Platformlar arası projelerde, bazı IntelliSense özellikleri, bir Android veya iOS bağlamında olsanız bile, paylaşılan kod projesindeki *. cpp* ve *. c* dosyalarında kullanılabilir.

Bu makalede C++ IntelliSense özelliklerine genel bakış sunulmaktadır. Projenizi IntelliSense için yapılandırma ve sorunları giderme hakkında daha fazla bilgi için bkz. [IntelliSense için C++ proje yapılandırma](visual-cpp-intellisense-configuration.md).

## <a name="intellisense-features-in-c"></a>İçindeki IntelliSense özellikleriC++

IntelliSense, kodlamayı daha kolay hale getirmek için bir özellik kümesine verilen addır. Farklı kişilerin ne kullanışlı olduğuna ilişkin farklı fikirleri olduğundan, IntelliSense özelliklerinin neredeyse tamamı **Seçenekler** iletişim kutusunda etkinleştirilebilir veya devre dışı bırakılabilir. böylece, **metin düzenleyici** ** > C++**  **Gelişmiş** > . **Seçenekler** iletişim kutusu, menü çubuğundaki **Araçlar** menüsünden kullanılabilir.

![Araç seçenekleri iletişim kutusu](../ide/media/sintellisensecpptoolsoptions.PNG)

IntelliSense 'e erişmek için aşağıdaki görüntüde gösterilen menü öğelerini ve klavye kısayollarını kullanabilirsiniz.

![IntelliSense menüsü](../ide/media/vs2015_cpp_intellisense_menu.png)

## <a name="statement-completion-and-member-list"></a>Ekstre tamamlama ve üye listesi

Bir anahtar sözcük, tür, işlev, değişken adı veya derleyicinin tanıdığı diğer program öğesini yazmaya başladığınızda, düzenleyici sizin için sözcüğü tamamlamayı önerir.

Simgelerin ve anlamlarıyla ilgili bir liste için, bkz. [sınıf görünümü ve nesne tarayıcısı simgeleri](../ide/class-view-and-object-browser-icons.md).

![Visual C&#43; &#43; tamamlanmış sözcük penceresi](../ide/media/vs2015_cpp_complete_word.png)

Üye listesini ilk kez çağırdığınızda, yalnızca geçerli bağlam için erişilebilen üyeleri gösterir. Bundan sonra **Ctrl**+**J** tuşlarına basarsanız, erişilebilirliğinden bağımsız olarak tüm üyeleri gösterir. Üçüncü kez çağırırsanız, daha geniş bir program öğeleri listesi gösterilir. **Seçenekler** iletişim kutusunda, **metin düzenleyici** > **C++ C/**  > **genel** > **otomatik liste üyeleri**' nin altındaki üye listesini devre dışı bırakabilirsiniz.

![Visual C&#43; &#43; üye listesi](../ide/media/vs2015_cpp_list_members.png)

## <a name="parameter-help"></a>Parametre yardımı

Bir işlev çağrısının açma ayracı veya bir sınıf şablonu değişken bildiriminde açılı ayraç yazdığınızda, düzenleyici, işlevin veya oluşturucunun her bir aşırı yüklemesiyle ilgili parametre türleriyle küçük bir pencere gösterir. "Current" parametresi imleç konumuna göre&mdash;&mdash;kalın. **Seçenekler** iletişim kutusunda parametre bilgilerini devre dışı bırakmak için **metin düzenleyici** > **C/C++**  > **genel** > **parametre bilgileri**' ni kullanabilirsiniz.

![Visual C&#43; &#43; parametresi yardımı](../ide/media/vs_2015_cpp_param_help.png)

## <a name="quick-info"></a>Hızlı Bilgi

Fare imlecini bir değişken üzerine getirdiğinizde, tür bilgilerini ve türün tanımlandığı üstbilgiyi gösteren küçük bir pencere satır içi görüntülenir. İşlevin imzasını görmek için bir işlev çağrısının üzerine gelin. **Seçenekler** iletişim kutusunda, **metin Düzenleyicisi** > **C++ C/**  > **Gelişmiş** > **otomatik hızlı bilgi**' nın altında bulunan hızlı bilgileri devre dışı bırakabilirsiniz.

![Visual C&#43; &#43; QuickInfo](../ide/media/vs2015_cpp_quickinfo.png)

## <a name="error-squiggles"></a>Hata dalgalı çizgiler

Dalgalı çizgiler bir program öğesi (değişken, anahtar sözcük, küme ayracı, tür adı vb.) altında bir hata veya koddaki olası bir hataya dikkat edin. Bir iletme bildirimi yazdığınızda, uygulamayı yazmanız gerektiğini hatırlatmak için yeşil bir dalgalı çizgi görünür. Şu anda etkin olmayan kodda bir hata olduğunda, örneğin Windows bağlamında çalışırken, ancak Android bağlamında bir hata olabilecek bir öğe girdiğinizde, bir paylaşılan projede mor renkli bir çizgi görünür. Kırmızı dalgalı çizgi, bir derleyici hatasını veya bir uyarı ile uğraşmanız gereken etkin kodda uyarı olduğunu gösterir.

![Visual C&#43; &#43; hatası dalgalı çizgiler](../ide/media/vs2015_cpp_error_quiggles.png)

### <a name="code-colorization-and-fonts"></a>Kod renklendirme ve yazı tipleri

Varsayılan renkler ve yazı tipleri, **Seçenekler** iletişim kutusunda, **ortam** > **yazı tipleri ve renkler**altında değiştirilebilir. Yalnızca düzenleyiciden değil, burada birçok UI penceresi için yazı tiplerini değiştirebilirsiniz. " C++ C++" İle başlamak için özel ayarlar diğer ayarlar tüm diller içindir.

## <a name="cross-platform-intellisense"></a>Platformlar arası IntelliSense

Paylaşılan bir kod projesinde, Android bağlamında çalışırken bile dalgalı çizgiler gibi bazı IntelliSense özellikleri kullanılabilir. Etkin olmayan bir projede hataya neden olacak bir kod yazarsanız, IntelliSense hala dalgalı çizgiler gösterir, ancak geçerli bağlamdaki hatalar için dalgalı çizgiler 'den farklı bir renkte yer alırlar.

Android ve iOS için derlemek üzere yapılandırılmış bir OpenGLES uygulaması düşünün. Çizim, düzenlenmekte olan paylaşılan kodu gösterir. Bu görüntüde, etkin proje **iOS. StaticLibrary**'dir:

![etkin proje olarak iOS seçilidir.](../ide/media/intellisensecppcrossplatform2.png)

Aşağıdakilere dikkat edin:

- `__ANDROID__` iOS projesi için tanımlanmadığı için, 6. satırdaki `#ifdef` dalı, etkin olmayan bir bölgeyi göstermek için gridir.

- 11. satırdaki tebrik değişkeni, artık kırmızı renkli bir çizgi olan `HELLO`tanımlayıcı ile başlatılır. Bunun nedeni, şu anda etkin olan iOS projesinde tanımlı `HELLO` tanımlayıcı değildir.

- Bu tanımlayıcı (Şu anda) etkin olmayan **Android. NativeActivity** projesinde tanımlanmadığı için, 12. satırın tanımlayıcı üzerinde mor renkli bir çizgi vardır `BYE`. Bu satır iOS etkin proje olduğunda derlense de, Android etkin proje olduğunda derlenmez. Bu paylaşılan kod olduğundan, geçerli etkin yapılandırmada derlense de kodu düzeltmeniz gerekir.

Etkin projeyi Android olarak değiştirirseniz dalgalı çizgiler değişikliği:

- `__ANDROID__` Android projesi için tanımlandığından, 8. satırdaki `#else` dalı, etkin olmayan bir bölgeyi gösterecek şekilde gri renkte.

- 11. satırdaki tebrik değişkeni, mor renkli bir çizgi olan tanımlayıcı `HELLO`ile başlatılır. Bunun nedeni, şu anda etkin olmayan iOS projesinde tanımlı `HELLO` tanımlayıcı değildir.

- Bu tanımlayıcı etkin projede tanımlanmadığı için, 12. satırda `BYE` tanımlayıcı üzerinde kırmızı renkli bir çizgi vardır.

## <a name="intellisense-for-stand-alone-files"></a>Tek başına dosyalar için IntelliSense

Herhangi bir projenin dışında tek bir dosya açtığınızda IntelliSense 'i yine de kullanmaya devam edersiniz. **Seçenekler** iletişim kutusunda, özel IntelliSense özelliklerini etkinleştirebilir veya devre dışı bırakabilirsiniz, **metin düzenleyici** ** > C++**  **Gelişmiş** > . IntelliSense 'i bir projenin parçası olmayan tek dosyalar için yapılandırmak üzere, **proje dışı dosyalar Için IntelliSense ve gözatma** bölümüne bakın.

![Visual C&#43; &#43; tek dosya IntelliSense](../ide/media/vs2015_cpp_single_file_intellisense.png)

Varsayılan olarak, tek dosya IntelliSense yalnızca üst bilgi dosyalarını bulmak için standart içerme dizinlerini kullanır. Daha fazla dizin eklemek için, **çözüm** düğümündeki kısayol menüsünü açın ve aşağıdaki çizimde gösterildiği gibi, dizini **hata ayıklama kaynak kodu** listesine ekleyin:

![Üst bilgi dosyasına bir yol ekleniyor.](../ide/media/intellisensedebugyourcode.jpg)

## <a name="enable-or-disable-features"></a>Özellikleri etkinleştirme veya devre dışı bırakma

Farklı kişilerin ne kullanışlı olduğuna ilişkin farklı fikirleri olduğundan, IntelliSense özelliklerinin neredeyse tamamı **Seçenekler** iletişim kutusunda etkinleştirilebilir veya devre dışı bırakılabilir. böylece, **metin düzenleyici** ** > C++**  **Gelişmiş** > . **Seçenekler** iletişim kutusu, menü çubuğundaki **Araçlar** menüsünden kullanılabilir.

![Araç seçenekleri iletişim kutusu](../ide/media/sintellisensecpptoolsoptions.PNG)

## <a name="see-also"></a>Ayrıca bkz.

- [IntelliSense Kullanma](../ide/using-intellisense.md)
- [IntelliSense için C++ bir proje yapılandırma](visual-cpp-intellisense-configuration.md)
