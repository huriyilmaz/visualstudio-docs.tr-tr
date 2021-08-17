---
title: Ayarlar kategorisi oluşturma | Microsoft Docs
description: bir Visual Studio settings kategorisi oluşturmayı ve bir ayarlar dosyasından değerleri kaydetmek ve geri yüklemek için kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- profile settings, creating categories
ms.assetid: 97c88693-05ff-499e-8c43-352ee073dcb7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: bbdc247e11930f05649b8e7b3c9d6d4cb1740aab
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122043719"
---
# <a name="create-a-settings-category"></a>Ayarlar kategorisi oluşturma

bu kılavuzda bir Visual Studio ayarları kategorisi oluşturup bir ayarlar dosyasından değerleri kaydetmek ve geri yüklemek için kullanabilirsiniz. Bir ayarlar kategorisi, "özel ayarlar noktası" olarak görünen ilgili özellikler grubudur. diğer bir deyişle, **içeri aktarma ve dışarı aktarma Ayarlar** sihirbazındaki onay kutusu olarak. ( **Araçları Araçlar** menüsünde bulabilirsiniz.) Ayarlar, bir kategori olarak kaydedilir veya geri yüklenir ve ayrı ayarlar sihirbazda gösterilmez. Daha fazla bilgi için bkz. [ortam ayarları](../ide/environment-settings.md).

Sınıfından türeterek bir ayarlar kategorisi oluşturursunuz <xref:Microsoft.VisualStudio.Shell.DialogPage> .

Bu yönergeyi başlatmak için önce [bir seçenek sayfası oluştur sayfasının](../extensibility/creating-an-options-page.md)ilk bölümünü tamamlamalısınız. Elde edilen seçenekler Özellik Kılavuzu, kategorideki özellikleri incelemenizi ve değiştirmenizi sağlar. Özellik kategorisini bir ayarlar dosyasına kaydettikten sonra, özellik değerlerinin nasıl depolandığını görmek için dosyayı inceleyebilirsiniz.

## <a name="prerequisites"></a>Önkoşullar
 Visual Studio 2015 ' den başlayarak, Visual Studio SDK 'sını indirme merkezi ' nden yüklemeyin. Visual Studio kurulum 'da isteğe bağlı bir özellik olarak eklenmiştir. VS SDK ' yı daha sonra da yükleyebilirsiniz. daha fazla bilgi için bkz. [Visual Studio SDK 'yı ınstall](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-settings-category"></a>Ayarlar kategorisi oluşturma
 Bu bölümde, ayarlar kategorisinin değerlerini kaydetmek ve geri yüklemek için özel bir ayar noktası kullanırsınız.

### <a name="to-create-a-settings-category"></a>Bir ayarlar kategorisi oluşturmak için

1. [Seçenek oluşturma sayfasını](../extensibility/creating-an-options-page.md)doldurun.

2. *VSPackage. resx* dosyasını açın ve şu üç dize kaynağını ekleyin:

    |Name|Değer|
    |----------|-----------|
    |106|Kategorim|
    |107|Ayarlar|
    |108|OptionInteger ve OptionFloat|

     bu, "kategorim" kategorisini, "my Ayarlar" nesnesini ve "optionınteger ve optionfloat" kategori açıklamasını oluşturan kaynakları oluşturur.

    > [!NOTE]
    > bu üçü de yalnızca kategori adı **Ayarlar içeri ve dışarı aktarma** sihirbazı 'nda görünmez.

3. *Myaraçları Optionspackage. cs* dosyasında, `float` `OptionFloat` `OptionPageGrid` Aşağıdaki örnekte gösterildiği gibi sınıfına adlı bir özellik ekleyin.

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
    > `OptionPageGrid`"Kategorim" adlı kategori, artık iki özelliklerden oluşur `OptionInteger` `OptionFloat` .

4. sınıfına bir ekleyin <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> `MyToolsOptionsPackage` ve CategoryName "kategorim" verin, bunu ObjectName "my Ayarlar" olarak verin ve isaraçları optionpage öğesini doğru olarak ayarlayın. CategoryResourceId, ObjectNameResourceID ve DescriptionResourceId değerlerini daha önce oluşturulan karşılık gelen dize kaynak kimliklerine ayarlayın.

    ```csharp
    [ProvideProfileAttribute(typeof(OptionPageGrid),
        "My Category", "My Settings", 106, 107, isToolsOptionPage:true, DescriptionResourceID = 108)]
    ```

5. Projeyi derleyin ve hata ayıklamayı başlatın. Deneysel örnekte, **kılavuz Sayfamın** şimdi tamsayı ve kayan değerleri olduğunu görmeniz gerekir.

## <a name="examine-the-settings-file"></a>Ayarlar dosyasını inceleyin
 Bu bölümde, özellik kategorisi değerlerini bir ayarlar dosyasına dışarı aktaralırsınız. Dosyayı incelemektir ve sonra değerleri özellik kategorisine geri aktarabilirsiniz.

1. **F5** tuşuna basarak projeyi hata ayıklama modunda başlatın. Bu, deneysel örneği başlatır.

2. **Araç**  >  **seçenekleri** iletişim kutusunu açın.

3. Sol bölmedeki ağaç görünümünde, **kategorim** ' ı genişletin ve ardından **kılavuz sayfam**' ı tıklatın.

4. **OptionFloat** değerini 3,1416 ve **OptionInteger** değerlerini 12 olarak değiştirin. **Tamam**'a tıklayın.

5. **araçlar** menüsünde **içeri aktar ve dışarı aktar Ayarlar**' a tıklayın.

     **Ayarlar içeri ve dışarı aktarma** sihirbazı görüntülenir.

6. **Seçili ortam ayarlarını dışa aktarma** seçeneğinin belirlendiğinden emin olun ve ardından **İleri**' ye tıklayın.

     **dışarı aktarılacak Ayarlar seçin** sayfası görüntülenir.

7. **Ayarlar** tıklayın.

     **Açıklama** **OptionInteger ve OptionFloat** olarak değişir.

8. **Ayarlar** seçili tek kategori olduğundan emin olun ve ardından **ileri**' ye tıklayın.

     **Ayarlar dosya sayfanızın adı** görüntülenir.

9. Yeni ayarlar dosyasını *MySettings. vssettings* olarak adlandırın ve uygun bir dizine kaydedin. **Finish (Son)** düğmesine tıklayın.

   `.vssettings`dosya Visual Studio ayarları dosyasıdır. Dosyanın şeması açık. En yaygın olarak, şema her kategorinin bir etiket olduğu bir XML yapısına uyar ve bu, kendisini alt kategori etiketleri içerebilir. Bu alt kategori etiketleri, özellik değeri etiketleri içerebilir. çoğu paket ortak yapıyı kullandığından, Visual Studio her bir paket, seçtiği şemayı içeren bir dosyaya rastgele XML katkıda bulunabilir.

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

12. **Araçlar** menüsünde **Seçenekler**' i tıklatın, **kategorim**' ı genişletin, **kılavuz** Sayfam ' ı tıklatın ve ardından **OptionFloat** değerini 1,0 ve **OptionInteger** olarak 1 olarak değiştirin. **Tamam**'a tıklayın.

13. **araçlar** menüsünde **içeri aktar ve dışarı aktar Ayarlar**, **seçili ortam ayarlarını içeri aktar**' ı seçin ve ardından **ileri**' ye tıklayın.

     **geçerli Ayarlar kaydet** sayfası görüntülenir.

14. **Hayır, yeni ayarları içeri aktar** ' ı seçin ve ardından **İleri**' ye tıklayın.

     **içeri aktarılacak Ayarlar koleksiyonunu seçin** sayfası görüntülenir.

15. ağaç görünümünün **Ayarlar** düğümündeki *mysettings. vssettings* dosyasını seçin. Dosya ağaç görünümünde görünmezse, **Araştır** ' a tıklayın ve bulun. **İleri**’ye tıklayın.

     **içeri aktarılacak Ayarlar seç** iletişim kutusu görüntülenir.

16. **Ayarlar** seçili olduğundan emin olun ve ardından **son**' a tıklayın. **Alma Tamam** sayfası göründüğünde **Kapat**' a tıklayın.

17. **Araçlar** menüsünde **Seçenekler**' e tıklayın, **kategorim**' i genişletin, **kılavuz** Sayfam ' a tıklayın ve özellik kategorisi değerlerinin geri yüklendiğini doğrulayın.
