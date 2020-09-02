---
title: Bir XCode projesini içeri aktarma | Microsoft Docs
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: aa4b8161-d98f-4a1a-9db3-520133bfc82f
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: 4faa2ecae7f53d29e6aad92723ca6d12e50e2812
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150945"
---
# <a name="import-an-xcode-project"></a>Bir XCode Projesini İçeri Aktarma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Platformlar arası mobil geliştirme için Microsoft Visual C++, XCode projelerinizi Visual Studio 'ya taşımaya yönelik destek içerir. burada, platformlar arası kitaplıklar oluşturabilir ve kodu diğer projelerle paylaşabilirsiniz. XCode 'dan Içeri aktarma Sihirbazı, projeleri içeri aktarma ve statik bir kitaplık veya paylaşılan kod projesi olarak kullanılmak üzere XCode Hedefinizdeki C++ kodunu bölme sürecini basitleştirir. Visual Studio 'da iOS 'a özgü kodunuzu yönetebilir ve film şeritleri ve yapılar yapmak için XCode kullanmaya devam edebilirsiniz. Visual Studio ile XCode arasında kolayca kod ve geri taşıma hakkında daha fazla bilgi için bkz. XCode ve Visual Studio arasında değişiklikleri taşıma.  
  
## <a name="using-the-import-from-xcode-wizard"></a>XCode 'Dan Içeri aktarma Sihirbazı 'nı kullanma  
 Bu konuda, kod paylaşımı ve platformlar arası çözümlerin avantajlarından yararlanmak için bir XCode projesini Visual Studio 'ya nasıl taşıyacağınız gösterilmektedir. Bir önkoşul olarak, projenizi içeri aktarabilmek, dışarı aktarmak ve derlemek için Mac 'i Visual Studio ile eşleştirmelidir. Eşleştirmeyi ayarlama hakkında yönergeler için bkz. [iOS kullanarak derlemek Için araçları yükleyip yapılandırma](../cross-platform/install-and-configure-tools-to-build-using-ios.md). Ayrıca Xcode projenizi ağ üzerinden paylaşmanız veya XCode 'dan Içeri aktarma Sihirbazı 'nı kullanmak için Visual Studio bilgisayarınıza taşımanız gerekir.  
  
#### <a name="import-from-xcode"></a>XCode 'dan içeri aktar  
  
1. **Dosya** menüsünde, **Yeni**, **içeri aktar**, **Xcode 'dan içeri aktar**' ı seçin. Bu, **XCode 'Dan Içeri aktarma** Sihirbazı 'nı başlatır.  
  
    ![İçeri aktarılacak XCode hedef projesini seçin](../cross-platform/media/cppmdd-u2-importxcode-choose.PNG "CPPMDD_U2_ImportXCode_Choose")  
  
2. **Bir proje seçin** bölmesinde, bir Xcode. PBXPROJ dosyası seçmek Için göz at düğmesini seçin. **XCode proje dosyası seç** iletişim kutusunda proje dosyasına gidin ve **Aç**' ı seçin.  
  
    ![Xcode proje dosyası seç iletişim kutusunda bir proje dosyası seçin](../cross-platform/media/cppmdd-u2-importxcode-browse.PNG "CPPMDD_U2_ImportXCode_Browse")  
  
    XCode 'dan Içeri aktar sihirbazında **İleri**' yi seçin.  
  
3. **Hedef hedefler** bölmesinde, Xcode projesinden, Visual Studio projelerine aktarılacak hedefleri seçin. XCode hedefleri, Visual Studio projelerine benzerdir; çoğu, bir ikili üreten kod ve kaynak koleksiyonudur. XCode 'dan Içeri aktarma Sihirbazı, hedef hedefleri olarak yalnızca ikili bir dosya üreten ve statik bir kitaplık olmayan hedeflerin içeri aktarmaya izin verir. XCode statik kitaplık hedefleri, bir sonraki adımın konusudur.  
  
    ![XCode sihirbazından içeri aktarma hedef hedefleri bölmesi](../cross-platform/media/cppmdd-u2-importxcode-destination.jpg "CPPMDD_U2_ImportXCode_Destination")  
  
    **Hedeflerin içeri aktarılacağı**her bir hedef için, sihirbaz ayrı bir statik kitaplık projesine bölünecek c++ kod dosyalarını otomatik olarak algılar ve bunları **c++ proje öğeleri** bölümüne koyar. Diğer kod ve kaynaklar **Xcode proje öğeleri** bölümünde bırakılır. Bunlar, sihirbaz içeri aktarma işlemini tamamladığında Visual Studio 'da ayrı statik kitaplık ve uygulama projeleri haline gelir. Varsayılan olarak, birim testi ve çerçeve hedefleri, sihirbaz tarafından ayrı projelere bölünmez.  
  
    Her projede hangi dosyaların olduğunu değiştirmek için yukarı ve aşağı düğmelerini kullanın. Her projedeki dosyalarla memnun kaldığınızda, devam etmek için **İleri** ' yi seçin.  
  
4. **Kitaplık hedefleri** bölmesinde, Xcode projesinden hangi statik kitaplığın hedeflediği, Visual Studio projelerine içeri aktarılacağını seçin. Bu bölmede, paylaşılan bir kod projesine hangi dosyaların yerleştirileceğini ve bir statik kitaplık projesine yerleştirilebilecek dosyaları seçebilirsiniz. **İçeri aktarılacak hedefler** listesindeki her bir hedef Içinde, **paylaşılan kod proje öğelerinde** ve **statik kitaplık proje öğelerinde** yukarı ve aşağı düğmelerini kullanarak hangi dosyaların yerleştirileceğini kontrol edebilirsiniz.  
  
    ![XCode kitaplığı hedefleri bölmesinden içeri aktar](../cross-platform/media/cppmdd-u2-importxcode-library.jpg "CPPMDD_U2_ImportXCode_Library")  
  
    Paylaşılan kod projesi, Visual Studio 'daki projeler arasında bir kaynak kod dosyaları kümesini paylaşmanın bir yoludur. Kod, kendisini içeren projenin bir parçası olarak oluşturulur. Paylaşılan kodu içeren projeler farklı mimarilere ve yapılandırmalara sahip olabileceğinden, bu, çok sayıda platformda oluşturulmuş olabilecek kodu içeren tek bir proje sağlamanın en iyi yoludur.  
  
    Her projedeki dosyalarla memnun kaldığınızda, devam etmek için **İleri** ' yi seçin.  
  
5. **Genel Özellikler** bölmesi, Visual Studio 'Daki tüm iOS projeleri için bir çerçeve arama yolu ve bir Ekle üst bilgi arama yolu ayarlamak üzere kullanılabilir. Visual Studio, kaynak kodu taraması ve IntelliSense için bu yolları kullanır. Bu genel yollar, ortak bir üstbilgiler ve çerçeveler kümesi kullanan iOS projeleri oluşturduğunuzda faydalıdır.  
  
    ![XCode Genel Özellikler bölmesinden içeri aktar](../cross-platform/media/cppmdd-u2-importxcode-global.jpg "CPPMDD_U2_ImportXCode_Global")  
  
    Bu genel yollar, **Seçenekler** Iletişim kutusunda Visual Studio 'da da ayarlanabilir. Bunları bulmak için, **Araçlar** menüsünde **Seçenekler**' i seçin. **Seçenekler** iletişim kutusunda **platformlar arası**, **C++**, **iOS**, **Genel Özellikler**' i genişletin.  
  
    Devam etmek için **İleri**’yi seçin.  
  
6. **Çerçeveler** bölmesi, Visual Studio tarafından, projeniz için göz atma ve IntelliSense için kullanılan yolları yapılandırmak için kullanılır. Yollar, XCode projeniz tarafından başvurulan her bir çerçeve için Visual Studio 'nun erişimine açık olmalıdır. Sihirbaz XCode projelerindeki çerçeve başvurularını denetler ve Visual Studio 'Nun Framework 'ü bulup bulamamadığını gösterir. Genel özelliklerde önceden ayarlamış olduğunuz herhangi bir yol Visual Studio tarafından keşfedilmelidir. Özel durumlar, çerçeveler listesinde listelenir. X ile listelenen her bir çerçeve için, Framework 'ü bulmak üzere Visual Studio için BILGISAYAR tarafından erişilebilir bir yol sağlayın. Yolu bulmak için **Klasör Seç** iletişim kutusunu kullanmak için [...] tarayıcı düğmesini kullanabilirsiniz. Çerçeve yolu, yerel bir kopyaya ya da Mac 'inizde ağa erişilebilen bir paylaşıma ait olabilir.  
  
    ![XCode çerçeveleri bölmesinden içeri aktar](../cross-platform/media/cppmdd-u2-importxcode-frameworks.jpg "CPPMDD_U2_ImportXCode_Frameworks")  
  
    Devam etmek için **İleri**’yi seçin.  
  
7. **Proje ayarları** bölmesi, sihirbazın oluşturduğu her proje için çerçeveyi değiştirmenize ve üst bilgi arama yolu ayarlarına dahil etmenize olanak tanır. Genel ayarlardan farklı projeye özgü yollar ayarlamak için bu bölmeyi kullanın.  
  
    Belirli bir proje için bir yol ayarlamak için, **hedef proje** açılır penceresinde, proje dosyasını seçin, ardından **Framework arama yolundaki** değerleri ayarlayın ve **başlık arama yolu denetimlerini ekleyin** . Yolu bulmak için bir **Klasör Seç** iletişim kutusunu kullanmak üzere her denetimin yanındaki [...] tarayıcı düğmesini kullanabilirsiniz.  
  
    ![XCode projeleri bölmesinden içeri aktar](../cross-platform/media/cppmdd-u2-importxcode-projects.jpg "CPPMDD_U2_ImportXCode_Projects")  
  
    Visual Studio 'da bu bılgısayarla eşlenmiş uzak Mac yoksa, uzak makine yapılandırma bağlantısı gösterilir. Eşleştirmeyi ayarlama hakkında yönergeler için bkz. [iOS kullanarak derlemek Için araçları yükleyip yapılandırma](../cross-platform/install-and-configure-tools-to-build-using-ios.md).  
  
    Sihirbaz ayarlarını kullanarak XCode projesini içeri aktarmak için **Içeri aktar**' ı seçin.  
  
   XCode 'dan Içeri aktarma Sihirbazı, Visual Studio 'da seçili XCode proje hedeflerine karşılık gelen projeler oluşturur. Diğer C++ projeleriyle paylaşılabilecek kod, ayrı paylaşılan koda ve statik kitaplık projelerine bölünür. Geri kalan kod, Visual Studio tarafından uzaktan yerleştirilebilecek iOS kitaplığı ve uygulama projelerine yerleştirilir. Kodu Visual Studio ve XCode arasında taşıma hakkında daha fazla bilgi için bkz. [XCode ve Visual Studio arasında eşitleme değişiklikleri](../cross-platform/sync-changes-between-xcode-and-visual-studio.md).
