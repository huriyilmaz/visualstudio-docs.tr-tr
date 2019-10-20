---
title: Görsel C++ IntelliSense | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 9d7c6414-4e6c-4889-a74c-a6033795eccc
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 173020a95977bdae2ad3006ce23dea376fb9d22e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72608819"
---
# <a name="visual-c-intellisense"></a>Visual C++ IntelliSense
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 2015 ' de IntelliSense, tek kod dosyaları ve projelerdeki dosyalar için de kullanılabilir. Platformlar arası projelerde, bazı IntelliSense özellikleri, Android veya iOS bağlamında olduğunuzda bile paylaşılan kod projesindeki. cpp ve. c dosyalarında kullanılabilir.

## <a name="intellisense-features-in-c"></a>İçindeki IntelliSense özellikleriC++
 IntelliSense, kodlamayı daha kolay hale getirmek için bir özellik kümesine verilen addır. Farklı kişilerin ne kullanışlı olduğuna ilişkin farklı fikirleri olduğundan, IntelliSense özelliklerinin neredeyse tamamı **metin düzenleyici, CC++/, gelişmiş** Özellik sayfasında etkinleştirilebilir veya devre dışı bırakılabilir.

 ![Araçlar, Seçenekler, metin düzenleyici, c&#47;c&#43;&#43;, gelişmiş](../ide/media/sintellisensecpptoolsoptions.PNG "sIntelliSenseCppToolsOptions")

 IntelliSense 'e erişmek için aşağıdaki görüntüde gösterilen menü öğelerini ve klavye kısayollarını kullanabilirsiniz.

 ![Visual C&#43; &#43; IntelliSense menüsü](../ide/media/vs2015-cpp-intellisense-menu.png "vs2015_cpp_intellisense_menu")

### <a name="statement-completion-and-member-list"></a>Ekstre tamamlama ve üye listesi
 Bir anahtar sözcük, tür, işlev, değişken adı veya derleyicinin tanıdığı diğer program öğesini yazmaya başladığınızda, düzenleyici sizin için sözcüğü tamamlamayı önerir

 Simgelerin ve anlamlarıyla ilgili bir liste için, bkz. [sınıf görünümü ve nesne tarayıcısı simgeleri](../ide/class-view-and-object-browser-icons.md).

 ![Visual C&#43; &#43; tamamlanmış sözcük penceresi](../ide/media/vs2015-cpp-complete-word.png "vs2015_cpp_complete_word")

 İlk kez üye listesi çağrıldığında yalnızca geçerli bağlam için erişilebilen Üyeler gösterilir. Bundan sonra **CTRL + J** kullanırsanız, erişilebilirliğinden bağımsız olarak tüm üyeleri gösterir. Üçüncü kez çağırırsanız, daha geniş bir program öğeleri listesi gösterilir. **C/C++ genel seçenekler** sayfasında deyimin tamamlanmasını devre dışı bırakabilirsiniz.

 ![Visual C&#43; &#43; üye listesi](../ide/media/vs2015-cpp-list-members.png "vs2015_cpp_list_members")

### <a name="parameter-help"></a>Parametre yardımı
 Bir işlev çağrısının açma ayracı veya bir sınıf şablonu değişken bildiriminde açılı ayraç yazdığınızda, düzenleyici, işlevin veya oluşturucunun her bir aşırı yüklemesiyle ilgili parametre türleriyle küçük bir pencere gösterir. "Current" parametresi, imleç konumuna göre--kalın. **C/C++ genel seçenekler** sayfasında deyimin tamamlanmasını devre dışı bırakabilirsiniz.

 ![Visual C&#43; &#43; parametresi yardımı](../ide/media/vs-2015-cpp-param-help.png "vs_2015_cpp_param_help")

### <a name="quick-info"></a>Hızlı Bilgi
 Fare imlecini bir değişken üzerine getirdiğinizde, tür bilgilerini ve türün tanımlandığı üstbilgiyi gösteren küçük bir pencere satır içi görüntülenir. İşlevin imzasını görmek için bir işlev çağrısının üzerine gelin. Hızlı bilgileri **metin düzenleyici, CC++/, gelişmiş** sayfasında devre dışı bırakabilirsiniz.

 ![Visual C&#43; &#43; QuickInfo](../ide/media/vs2015-cpp-quickinfo.png "vs2015_cpp_quickInfo")

## <a name="error-squiggles"></a>Hata dalgalı çizgiler
 Dalgalı çizgiler bir program öğesi (değişken, anahtar sözcük, küme ayracı, tür adı vb.) altında bir hata veya koddaki olası bir hataya dikkat edin. Bir iletme bildirimi yazdığınızda, uygulamayı yazmanız gerektiğini hatırlatmak için yeşil bir dalgalı çizgi görünür. Şu anda etkin olmayan kodda bir hata olduğunda, örneğin Windows bağlamında çalışırken, ancak Android bağlamında bir hata olabilecek bir öğe girdiğinizde, bir paylaşılan projede mor renkli bir çizgi görünür. Kırmızı dalgalı çizgi, bir derleyici hatasını veya bir uyarı ile uğraşmanız gereken etkin kodda uyarı olduğunu gösterir.

 ![Visual C&#43; &#43; hatası dalgalı çizgiler](../ide/media/vs2015-cpp-error-quiggles.png "vs2015_cpp_error_quiggles")

## <a name="code-colorization-and-fonts"></a>Kod renklendirme ve yazı tipleri
 Varsayılan renkler ve yazı tipleri, **ortam, yazı tipleri ve renkler** Özellik sayfası kullanılarak değiştirilebilir. Yalnızca düzenleyiciden değil, burada birçok UI penceresi için yazı tiplerini değiştirebilirsiniz. " C++ C++" İle başlamak için özel ayarlar diğer ayarlar tüm diller içindir.

## <a name="cross-platform-intellisense"></a>Platformlar arası IntelliSense
 Paylaşılan bir kod projesinde, Android bağlamında çalışırken bile dalgalı çizgiler gibi bazı IntelliSense özellikleri kullanılabilir. Etkin olmayan bir projede hataya neden olacak bir kod yazarsanız, IntelliSense hala dalgalı çizgiler gösterir, ancak geçerli bağlamdaki hatalar için dalgalı çizgiler 'den farklı bir renkte yer alırlar.

 Android ve iOS için derlemek üzere yapılandırılmış bir OpenGLES uygulaması aşağıda verilmiştir. Çizim, düzenlenmekte olan paylaşılan kodu gösterir. İlk görüntüde, Android etkin projem:

 ![Android projesi etkin projem dir.](../ide/media/intellisensecppcrossplatform.png "Intellisensecpphandshake Splatform")

 Aşağıdakilere dikkat edin:

- @No__t_0 Android projesi için tanımlandığından, 8. satırdaki #else dalı, etkin olmayan bölge olduğunu göstermek için gridir.

- 11. satırda bulunan selamlama değişkeni, mor renkli bir çizgi olan tanıtıcı Merhaba ile başlatılır. Bunun nedeni, şu anda etkin olmayan iOS projesinde hiçbir tanımlayıcı HELLO tanımlanmamaktadır. Android proje satırı 11 derlenmesi sırasında, iOS 'ta olmayacaktır. Bu paylaşılan kod olduğundan, bu, geçerli etkin yapılandırmada derlense de değiştirmeniz gereken bir şeydir.

- 12. satırda, BYE tanımlayıcıda kırmızı dalgalı çizgi vardır. Bu tanımlayıcı Şu anda seçili etkin projede tanımlı değil.

  Şimdi, etkin projeyi iOS. StaticLibrary olarak değiştirin ve dalgalı çizgiler nasıl değişdiğine dikkat edin.

  ![etkin proje olarak iOS seçilidir.](../ide/media/intellisensecppcrossplatform2.png "IntelliSenseCppCrossPlatform2")

  Aşağıdakilere dikkat edin:

- İOS projesi için *_Android \\* \_ tanımlanmadığı için 6. satırdaki #ifdef dalı, etkin olmayan bölge olduğunu göstermek için gridir.

- 11. satırdaki tebrik değişkeni, artık kırmızı dalgalı çizgi olan tanıtıcı Merhaba ile başlatılır. Bunun nedeni, şu anda etkin olan iOS projesinde hiçbir tanımlayıcı HELLO tanımlanmamaktadır.

- 12. satırda mor çizgi, BYE tanımlayıcısı üzerinde. Bu tanımlayıcı Şu anda etkin olmayan Android. NativeActivity projesinde tanımlı değil.

## <a name="single-file-intellisense"></a>Tek dosya IntelliSense
 Herhangi bir projenin dışında tek bir dosya açtığınızda IntelliSense 'i yine de kullanmaya devam edersiniz. IntelliSense özelliklerini açmak veya kapatmak için **metin düzenleyici, CC++/, gelişmiş** 'e giderek belirli özellikleri etkinleştirebilir veya devre dışı bırakabilirsiniz. IntelliSense 'i bir projenin parçası olmayan tek dosyalara yönelik olarak yapılandırmak için, **Gelişmiş** bölümünde **proje dışı dosyalar Için IntelliSense ve göz atma** ' ı arayın. Bkz [. C++ görsel Kılavuzlu Tur](https://msdn.microsoft.com/499cb66f-7df1-45d6-8b6b-33d94fd1f17c).

 ![Visual C&#43; &#43; tek dosya IntelliSense](../ide/media/vs2015-cpp-single-file-intellisense.png "vs2015_cpp_single_file_intellisense")

 Varsayılan olarak, tek dosya IntelliSense yalnızca üst bilgi dosyalarını bulmak için standart içerme dizinlerini kullanır. Daha fazla dizin eklemek için, çözüm düğümündeki kısayol menüsünü açın ve aşağıdaki çizimde gösterildiği gibi, dizini **hata ayıklama kaynak kodu** listesine ekleyin:

 ![Üst bilgi dosyasına bir yol ekleniyor.](../ide/media/intellisensedebugyourcode.jpg "Intellisensedebugyourcode")

## <a name="see-also"></a>Ayrıca Bkz.
 [IntelliSense Kullanma](../ide/using-intellisense.md)
