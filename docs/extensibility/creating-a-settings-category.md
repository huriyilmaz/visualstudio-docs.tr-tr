---
title: Ayarlar kategorisi oluşturma | Microsoft Docs
description: Bir Visual Studio ayarları kategorisi oluşturmayı ve bir ayarlar dosyasından değerleri kaydetmek ve geri yüklemek için kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- profile settings, creating categories
ms.assetid: 97c88693-05ff-499e-8c43-352ee073dcb7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: bf089eeaf8c4408a0bc76d2f3982d311ac9c5979
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99896266"
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

     Bu, "kategorim" kategorisini, "ayarlarımı My" nesnesini ve "OptionInteger ve OptionFloat" Kategori açıklamasını oluşturan kaynakları oluşturur.

    > [!NOTE]
    > Bu üçü de yalnızca kategori adı, **içeri ve dışarı aktarma ayarları** sihirbazında görünmez.

3. *MyToolsOptionsPackage.cs*' de, `float` `OptionFloat` `OptionPageGrid` Aşağıdaki örnekte gösterildiği gibi sınıfına adlı bir özellik ekleyin.

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

4. Sınıfına bir ekleyin <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> `MyToolsOptionsPackage` ve CategoryName "kategorim" verin, bunu ObjectName "My Settings" olarak ayarlayın ve Isaraçları OptionPage öğesini true olarak ayarlayın. CategoryResourceId, ObjectNameResourceID ve DescriptionResourceId değerlerini daha önce oluşturulan karşılık gelen dize kaynak kimliklerine ayarlayın.

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

5. **Araçlar** menüsünde **Içeri ve dışarı aktarma ayarları**' na tıklayın.

     **Ayarları içeri ve dışarı aktarma** Sihirbazı görüntülenir.

6. **Seçili ortam ayarlarını dışa aktarma** seçeneğinin belirlendiğinden emin olun ve ardından **İleri**' ye tıklayın.

     **Dışarı aktarılacak ayarları seçin** sayfası görüntülenir.

7. Ayarlarım **' ı** tıklatın.

     **Açıklama** **OptionInteger ve OptionFloat** olarak değişir.

8. **Ayarlarım '** ın seçili tek kategori olduğundan emin olun ve ardından **İleri**' ye tıklayın.

     **Ayarlar dosyanızın adı** sayfası görüntülenir.

9. Yeni ayarlar dosyasını *MySettings. vssettings* olarak adlandırın ve uygun bir dizine kaydedin. **Finish (Son)** düğmesine tıklayın.

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

13. **Araçlar** menüsünde **Içeri ve dışarı aktarma ayarları**' na tıklayın, **Seçili ortam ayarlarını içeri aktar**' ı seçin ve ardından **İleri**' ye tıklayın.

     **Geçerli ayarları Kaydet** sayfası görüntülenir.

14. **Hayır, yeni ayarları içeri aktar** ' ı seçin ve ardından **İleri**' ye tıklayın.

     **Alınacak ayarların bir koleksiyonunu seçin** sayfası görüntülenir.

15. Ağaç görünümünün **ayarlarım düğümündeki** *MySettings. vssettings* dosyasını seçin. Dosya ağaç görünümünde görünmezse, **Araştır** ' a tıklayın ve bulun. **İleri**’ye tıklayın.

     **Alınacak ayarları seçin** iletişim kutusu görüntülenir.

16. **Ayarlarım ' ın seçili** olduğundan emin olun ve ardından **son**' a tıklayın. **Alma Tamam** sayfası göründüğünde **Kapat**' a tıklayın.

17. **Araçlar** menüsünde **Seçenekler**' e tıklayın, **kategorim**' i genişletin, **kılavuz** Sayfam ' a tıklayın ve özellik kategorisi değerlerinin geri yüklendiğini doğrulayın.
