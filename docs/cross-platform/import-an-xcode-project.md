---
title: Bir Xcode projesini içeri aktarma | Microsoft Docs
ms.custom: ''
ms.date: 10/17/2019
ms.topic: conceptual
ms.assetid: aa4b8161-d98f-4a1a-9db3-520133bfc82f
ms.technology: vs-ide-mobile
author: corob-msft
ms.author: corob
manager: jillfra
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: 62161b612d6c4583cd2206c3d18dc6606d2d9f0b
ms.sourcegitcommit: 8a96a65676fd7a2a03b0803d7eceae65f3fa142b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72588889"
---
# <a name="import-an-xcode-project"></a>Xcode projesini içeri aktarma

Platformlar arası mobil geliştirme için Visual Studio Araçları, Xcode C++ projelerinizi Visual Studio 'ya taşımaya yönelik destek içerir. Bunlar arasında platformlar arası kitaplıklar oluşturabilir ve kodu diğer projelerle paylaşabilirsiniz. Xcode 'dan Içeri aktarma Sihirbazı, projeleri içeri aktarma ve statik bir kitaplık veya paylaşılan C++ kod projesi olarak kullanılmak üzere Xcode Hedefinizdeki kodu bölme sürecini basitleştirir. Visual Studio 'da iOS 'a özgü kodunuzu yönetebilir ve film şeritleri ve yapılar yapmak için Xcode kullanmaya devam edebilirsiniz. Visual Studio ile Xcode arasında kolayca kod ve geri taşıma hakkında daha fazla bilgi için bkz. [Xcode ve Visual Studio arasında eşitleme değişiklikleri](sync-changes-between-xcode-and-visual-studio.md).

## <a name="use-the-import-from-xcode-wizard"></a>Xcode 'Dan Içeri aktarma Sihirbazı 'nı kullanma

Bu makalede, kod paylaşımı ve platformlar arası çözümlerin avantajlarından yararlanmak için bir Xcode projesini Visual Studio 'ya nasıl taşıyacağınız gösterilmektedir. Bir önkoşul olarak, projenizi içeri aktarmak, dışarı aktarmak ve derlemek için Mac 'i Visual Studio ile eşleştirmelidir. Eşleştirmeyi ayarlama hakkında yönergeler için bkz. [iOS kullanarak derlemek için araçları yükleyip yapılandırma](../cross-platform/install-and-configure-tools-to-build-using-ios.md). Ayrıca Xcode projenizi ağ üzerinden paylaşmanız veya Xcode 'dan Içeri aktarma Sihirbazı 'nı kullanabilmeniz için Visual Studio bilgisayarınıza taşımanız gerekir.

### <a name="import-from-xcode"></a>Xcode 'dan içeri aktar

1. **Dosya** menüsünde, **Yeni**, **içeri aktar**, **Xcode 'dan içeri aktar**' ı seçin. Bu komut **Xcode 'Dan Içeri aktarma** Sihirbazı 'nı başlatır.

   ![İçeri aktarılacak Xcode hedef projesini seçin](../cross-platform/media/cppmdd_u2_importxcode_choose.PNG "İçeri aktarılacak Xcode hedef projesini seçin")

1. **Bir proje seçin** bölmesinde, bir Xcode *. PBXPROJ* dosyası seçmek için göz at düğmesini seçin. **Xcode proje dosyası seç** iletişim kutusunda proje dosyasına gidin ve **Aç**' ı seçin.

   ![Xcode proje dosyası seç iletişim kutusunda bir proje dosyası seçin](../cross-platform/media/cppmdd_u2_importxcode_browse.PNG "Xcode proje dosyası seç iletişim kutusunda bir proje dosyası seçin")

   Xcode 'dan Içeri aktar sihirbazında **İleri**' yi seçin.

1. **Hedef hedefler** bölmesinde, Xcode projesinden, Visual Studio projelerine aktarılacak hedefleri seçin. Xcode hedefleri, Visual Studio projelerine benzerdir; çoğu, bir ikili üreten kod ve kaynak koleksiyonudur. Xcode 'dan Içeri aktarma Sihirbazı, hedef hedefleri olarak yalnızca ikili bir dosya üreten ve statik bir kitaplık olmayan hedeflerin içeri aktarmaya izin verir. Xcode statik kitaplık hedefleri, bir sonraki adımın konusudur.

   ![Xcode sihirbazından içeri aktarma hedef hedefleri bölmesi](../cross-platform/media/cppmdd_u2_importxcode_destination.jpg "Xcode sihirbazından içeri aktarma hedef hedefleri bölmesi")

   **Hedeflerin içeri aktarılacağı**her bir hedef için, sihirbaz ayrı bir statik kitaplık C++ projesine bölünecek kod dosyalarını otomatik olarak algılar ve bunları  **C++ proje öğeleri** bölümüne koyar. Diğer kod ve kaynaklar **Xcode proje öğeleri** bölümünde bırakılır. Bunlar, sihirbaz içeri aktarma işlemini tamamladığında Visual Studio 'da ayrı statik kitaplık ve uygulama projeleri haline gelir. Varsayılan olarak, birim testi ve çerçeve hedefleri, sihirbaz tarafından ayrı projelere bölünmemektedir.

   Her projede hangi dosyaların olduğunu değiştirmek için yukarı ve aşağı düğmelerini kullanın. Her projedeki dosyalarla memnun kaldığınızda, devam etmek için **İleri** ' yi seçin.

1. **Kitaplık hedefleri** bölmesinde, Xcode projesinden hangi statik kitaplığın hedeflediği, Visual Studio projelerine içeri aktarılacağını seçin. Bu bölmede, paylaşılan bir kod projesine hangi dosyaların yerleştirileceğini ve bir statik kitaplık projesine yerleştirileceğini seçebilirsiniz. **İçeri aktarılacak hedefler** listesindeki her bir hedef Içinde, **paylaşılan kod proje öğelerinde** ve **statik kitaplık proje öğelerinde** yukarı ve aşağı düğmelerini kullanarak hangi dosyaların yerleştirileceğini kontrol edebilirsiniz.

   ![Xcode kitaplığı hedefleri bölmesinden içeri aktar](../cross-platform/media/cppmdd_u2_importxcode_library.jpg "Xcode kitaplığı hedefleri bölmesinden içeri aktar")

   Paylaşılan kod projesi, Visual Studio 'daki projeler arasında bir kaynak dosya kümesini paylaşmanın bir yoludur. Kod, kendisini içeren projenin bir parçası olarak oluşturulur. Paylaşılan kodu içeren projeler farklı mimarilere ve yapılandırmalara sahip olabilir. Paylaşılan bir kod projesi, çok sayıda platform için oluşturulmuş olabilecek kodu içeren tek bir proje sağlamanın en iyi yoludur.

   Her projedeki dosyalarla memnun kaldığınızda, devam etmek için **İleri** ' yi seçin.

1. Visual Studio 'daki tüm iOS projeleri için bir çerçeve arama yolu ve bir Ekle üst bilgi arama yolu ayarlamak için **Genel Özellikler** bölmesini kullanın. Visual Studio, kaynak kodu taraması ve IntelliSense için bu yolları kullanır. Bu genel yollar, ortak bir üstbilgiler ve çerçeveler kümesi kullanan iOS projeleri oluşturduğunuzda faydalıdır.

   ![Xcode Genel Özellikler bölmesinden içeri aktar](../cross-platform/media/cppmdd_u2_importxcode_global.jpg "Xcode Genel Özellikler bölmesinden içeri aktar")

   Bu genel yollar, **Seçenekler** Iletişim kutusunda Visual Studio 'da da ayarlanabilir. Bunları bulmak için, **Araçlar** menüsünde **Seçenekler**' i seçin. **Seçenekler** iletişim kutusunda,  > **C++** **platformlar arası**  > **iOS**  > **Genel Özellikler**' i genişletin.

   Devam etmek için **İleri ' yi** seçin.

1. **Çerçeveler** bölmesi, Visual Studio tarafından, projeniz için göz atma ve IntelliSense için kullanılan yolları yapılandırmak için kullanılır. Yollar, Xcode projeniz tarafından başvurulan her bir çerçeve için Visual Studio 'nun erişimine açık olmalıdır. Sihirbaz Xcode projelerindeki çerçeve başvurularını denetler ve Visual Studio 'Nun Framework 'ü bulup bulamamadığını gösterir. Genel özelliklerde önceden ayarlamış olduğunuz herhangi bir yol Visual Studio tarafından keşfedilmelidir. Özel durumlar, çerçeveler listesinde listelenir. X ile listelenen her bir çerçeve için, Framework 'ü bulmak üzere Visual Studio için BILGISAYAR tarafından erişilebilir bir yol sağlayın. Yolu bulmak için bir **Klasör Seç** iletişim kutusunu kullanmak için, tarayıcı düğmesini **...** seçeneğini kullanabilirsiniz. Çerçeve yolu, yerel bir kopyaya ya da Mac 'inizde ağa erişilebilen bir paylaşıma ait olabilir.

   ![Xcode çerçeveleri bölmesinden içeri aktar](../cross-platform/media/cppmdd_u2_importxcode_frameworks.jpg "Xcode çerçeveleri bölmesinden içeri aktar")

   Devam etmek için **İleri ' yi** seçin.

1. **Proje ayarları** bölmesi, sihirbazın oluşturduğu her proje için çerçeveyi değiştirmenize ve üst bilgi arama yolu ayarlarına dahil etmenize olanak tanır. Genel ayarlardan farklı projeye özgü yollar ayarlamak için bu bölmeyi kullanın.

   Belirli bir proje için bir yol ayarlamak için, **hedef proje** açılır penceresinde, proje dosyasını seçin. Ardından, **Framework arama yolundaki** değerleri ayarlayın ve **üstbilgi arama yolu denetimlerini ekleyin** . Yolu bulmak için bir **Klasör Seç** iletişim kutusunu kullanmak üzere her bir denetimin yanındaki **Git düğmesini kullanabilirsiniz.**

   ![Xcode projeleri bölmesinden içeri aktar](../cross-platform/media/cppmdd_u2_importxcode_projects.jpg "Xcode projeleri bölmesinden içeri aktar")

   Visual Studio 'da bu bılgısayarla eşlenmiş uzak Mac yoksa, **uzak makine yapılandırma** bağlantısı gösterilir. Eşleştirmeyi ayarlama hakkında yönergeler için bkz. [iOS kullanarak derlemek için araçları yükleyip yapılandırma](../cross-platform/install-and-configure-tools-to-build-using-ios.md).

   Sihirbaz ayarlarını kullanarak Xcode projesini içeri aktarmak için **Içeri aktar**' ı seçin.

   Xcode 'dan Içeri aktarma Sihirbazı, Visual Studio 'da seçili Xcode proje hedeflerine karşılık gelen projeler oluşturur. Diğer C++ projelerle paylaşılabilecek kod, ayrı paylaşılan koda ve statik kitaplık projelerine bölünür. Geri kalan kod, Visual Studio tarafından uzaktan yerleştirilebilecek iOS kitaplığı ve uygulama projelerine yerleştirilir. Kodu Visual Studio ve Xcode arasında taşıma hakkında daha fazla bilgi için bkz. [Xcode ve Visual Studio arasında eşitleme değişiklikleri](../cross-platform/sync-changes-between-xcode-and-visual-studio.md).

## <a name="see-also"></a>Ayrıca bkz.

- [İle platformlar arası mobil geliştirmeC++](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md)
