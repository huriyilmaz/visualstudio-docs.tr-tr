---
title: Ayarlar kategorisi oluşturma | Microsoft Docs
description: Bir Visual Studio ayarları kategorisi oluşturmayı ve bir ayarlar dosyasından değerleri kaydetmek ve geri yüklemek için kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- profile settings, creating categories
ms.assetid: 97c88693-05ff-499e-8c43-352ee073dcb7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: fe46ea835a119978fd3decd26949db3d59944e5e
ms.sourcegitcommit: 63cb90e8cea112aa2ce8741101b309dbc709e393
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/29/2021
ms.locfileid: "110687613"
---
# <a name="create-a-settings-category"></a>Ayarlar kategorisi oluşturma

Bu kılavuzda, bir Visual Studio ayarları kategorisi oluşturup bir ayarlar dosyasından değerleri kaydetmek ve geri yüklemek için kullanabilirsiniz. Bir ayarlar kategorisi, "özel ayarlar noktası" olarak görünen ilgili özellikler grubudur. diğer bir deyişle, **Ayarları içeri ve dışarı** Aktarma Sihirbazı ' nda bir onay kutusu olarak. ( **Araçları Araçlar** menüsünde bulabilirsiniz.) Ayarlar bir kategori olarak kaydedilir veya geri yüklenir ve ayrı ayarlar sihirbazda görüntülenmez. Daha fazla bilgi için bkz. [ortam ayarları](../ide/environment-settings.md).

Sınıfından türeterek bir ayarlar kategorisi oluşturursunuz <xref:Microsoft.VisualStudio.Shell.DialogPage> .

Bu yönergeyi başlatmak için önce [bir seçenek sayfası oluştur sayfasının](../extensibility/creating-an-options-page.md)ilk bölümünü tamamlamalısınız. Elde edilen seçenekler Özellik Kılavuzu, kategorideki özellikleri incelemenizi ve değiştirmenizi sağlar. Özellik kategorisini bir ayarlar dosyasına kaydettikten sonra, özellik değerlerinin nasıl depolandığını görmek için dosyayı inceleyebilirsiniz.

## <a name="prerequisites"></a>Önkoşullar
 Visual Studio 2015 ' den başlayarak, Visual Studio SDK 'sını indirme merkezinden yüklememeyin. Visual Studio kurulumuna isteğe bağlı bir özellik olarak dahildir. VS SDK ' yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için bkz. [Visual Studio SDK 'Yı yüklemeyi](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-settings-category"></a>Ayarlar kategorisi oluşturma
 Bu bölümde, ayarlar kategorisinin değerlerini kaydetmek ve geri yüklemek için özel bir ayar noktası kullanırsınız.

### <a name="to-create-a-settings-category"></a>Bir ayarlar kategorisi oluşturmak için

1. [Seçenek oluşturma sayfasını](../extensibility/creating-an-options-page.md)doldurun.

2. *VSPackage. resx* dosyasını açın ve şu üç dize kaynağını ekleyin:

    |Name|Değer|
    |----------|-----------|
    |106|Kategorim|
    |107|Ayarlarım|
    |108|OptionInteger ve OptionFloat|

     Bu, kategoriye "Kategorim" adını, "Ayarlarım" nesnesini ve "OptionInteger ve OptionFloat" kategori açıklamasını oluşturan kaynaklar oluşturur.

    > [!NOTE]
    > Bu üçü arasında, Ayarları İçeri ve Dışarı Aktarma sihirbazında yalnızca **kategori adı görünmez.**

3. *MyToolsOptionsPackage.cs* içinde, aşağıdaki örnekte gösterildiği gibi `float` `OptionFloat` `OptionPageGrid` sınıfına adlı bir özellik ekleyin.

    ```csharp
    public class OptionPageGrid : DialogPage
    {
        private int optionInt = 256;
        private float optionFloat = 3.14F;

        [Category("My Options")]
        [DisplayName("My Integer option")]
        [Description("My integer option")]
        public int OptionInteger
        {
            get { return optionInt; }
            set { optionInt = value; }
        }
        [Category("My Options")]
        [DisplayName("My Float option")]
        [Description("My float option")]
        public float OptionFloat
        {
            get { return optionFloat; }
            set { optionFloat = value; }
        }
    }
    ```

    > [!NOTE]
    > `OptionPageGrid`"Kategorim" adlı kategori artık ve olmak için iki özellik `OptionInteger` `OptionFloat` içerir.

4. sınıfına <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> bir ekleyin ve `MyToolsOptionsPackage` CategoryName "My Category" girin, ObjectName "My Settings" yazın ve isToolsOptionPage'i true olarak ayarlayın. categoryResourceID, objectNameResourceID ve DescriptionResourceID'yi daha önce oluşturulan karşılık gelen dize kaynağı kimlikleri olarak ayarlayın.

    ```csharp
    [ProvideProfileAttribute(typeof(OptionPageGrid),
        "My Category", "My Settings", 106, 107, isToolsOptionPage:true, DescriptionResourceID = 108)]
    ```

5. Projeyi derleme ve hata ayıklamayı başlatma. Deneysel örnekte Kılavuzum Sayfasının artık **hem tamsayı hem** de kayan değerlere sahip olduğunu görüyoruz.

## <a name="examine-the-settings-file"></a>Ayarlar dosyasını inceleme
 Bu bölümde, özellik kategorisi değerlerini bir ayarlar dosyasına dışarı aktarın. Dosyayı inceler ve ardından değerleri özellik kategorisine geri içeri aktarabilirsiniz.

1. F5 tuşuna basarak projeyi hata ayıklama **modunda başlatın.** Bu, deneysel örneği başlatır.

2. Araçlar Seçenekleri **iletişim**  >  **kutusunu** açın.

3. Sol bölmedeki ağaç görünümünde Kategorim'i genişletin ve **ardından** Kılavuz **Sayfam'a tıklayın.**

4. **OptionFloat değerini** 3,1416 ve **OptionInteger değerini** 12 olarak değiştirir. **Tamam**'a tıklayın.

5. Araçlar menüsünde **Ayarları** İçeri ve Dışarı **Aktar'a tıklayın.**

     **Ayarları içeri ve dışarı aktarma** Sihirbazı görüntülenir.

6. **Seçili ortam ayarlarını dışa aktarma** seçeneğinin belirlendiğinden emin olun ve ardından **İleri**' ye tıklayın.

     **Dışarı aktarılacak ayarları seçin** sayfası görüntülenir.

7. Ayarlarım **' ı** tıklatın.

     **Açıklama** **OptionInteger ve OptionFloat** olarak değişir.

8. **Ayarlarım '** ın seçili tek kategori olduğundan emin olun ve ardından **İleri**' ye tıklayın.

     **Ayarlar dosyanızın adı** sayfası görüntülenir.

9. Yeni ayarlar dosyasını *MySettings. vssettings* olarak adlandırın ve uygun bir dizine kaydedin. **Finish (Son)** düğmesine tıklayın.

   `.vssettings`Dosya, Visual Studio ayarları dosyasıdır. Dosyanın şeması açık. En yaygın olarak, şema her kategorinin bir etiket olduğu bir XML yapısına uyar ve bu, kendisini alt kategori etiketleri içerebilir. Bu alt kategori etiketleri, özellik değeri etiketleri içerebilir. Çoğu paket ortak yapıyı kullandığından, Visual Studio 'daki herhangi bir paket, tarafından seçtiği şemayı kullanarak rastgele XML 'yi dosyaya katkıda bulunabilir.

   **Dışarı aktarma tamamlandı** sayfası, ayarlarınızın başarıyla verildiğini bildiriyor.

10. **Dosya** menüsünde **Aç**' ın üzerine gelin ve ardından **Dosya**' ya tıklayın. *MySettings. vssettings* ' i bulun ve açın.

     Dosyanın aşağıdaki bölümüne verdiğiniz özellik kategorisini (GUID 'lerinizin farklı olacağı) bulabilirsiniz.

    ```
    <Category name="My Category_My Settings"
          Category="{4802bc3e-3d9d-4591-8201-23d1a05216a6}"
          Package="{6bb6942e-014c-489e-a612-a935680f703d}"
          RegisteredName="My Category_My Settings">
          PackageName="MyToolsOptionsPackage">
       <PropertyValue name="OptionFloat">3.1416</PropertyValue>
       <PropertyValue name="OptionInteger">12</PropertyValue>
    </Category>
    ```

     Tam kategori adının, kategori adına alt çizgi eklenerek ve ardından nesne adından oluşturulduğuna dikkat edin. OptionFloat ve OptionInteger kategori içinde, kendilerine ait değerleriyle birlikte görüntülenir.

11. Ayarları değiştirmeden ayarlar dosyasını kapatın.

12. Araçlar menüsünde **Seçenekler'e** tıklayın, Kategorim'i **genişletin,** Kılavuz Sayfam'a tıklayın ve **OptionFloat** değerini 1.0 ve **OptionInteger** değerini 1 olarak ayarlayın.   **Tamam**'a tıklayın.

13. Araçlar **menüsünde, Ayarları** İçeri ve Dışarı **Aktar'a tıklayın,** Seçili ortam ayarlarını içeri aktar'ı **seçin** ve ardından Sonraki'ye **tıklayın.**

     Geçerli **Ayarları Kaydet** sayfası görüntülenir.

14. **Hayır'ı seçin, yeni ayarları içeri aktarın ve** ardından Sonraki'ye **tıklayın.**

     İçeri **Aktar için Ayarlar Koleksiyonu Seçin** sayfası görüntülenir.

15. Ağaç *görünümünün Ayarlarım düğümünde MySettings.vssettings* dosyasını seçin.  Dosya ağaç görünümünde görünmüyorsa Gözat'a **tıklayın** ve dosyayı bulun. **İleri**’ye tıklayın.

     İçeri **Aktar için Ayarları Seç** iletişim kutusu görüntülenir.

16. Ayarlarım'ın **seçili olduğundan** emin olun ve ardından Son'a **tıklayın.** Tamamlandı İçeri **Aktar sayfası görüntülendiğinde** Kapat'a **tıklayın.**

17. Araçlar menüsünde **Seçenekler'e** **tıklayın,** **Kategorim'i** genişletin, **Kılavuz** Sayfam'a tıklayın ve özellik kategorisi değerlerinin geri yüklendiklerini doğrulayın.
