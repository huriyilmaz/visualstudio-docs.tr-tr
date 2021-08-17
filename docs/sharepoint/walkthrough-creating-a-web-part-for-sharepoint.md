---
title: 'Adım adım kılavuz: SharePoint | için Web Bölümü Oluşturma Microsoft Docs'
description: SharePoint için bir web bölümü oluşturun. Web bölümleri, kullanıcıların bir tarayıcı kullanarak site sayfalarının içeriğini, SharePoint davranışını doğrudan değiştirmesine olanak sağlar.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Web Parts [SharePoint development in Visual Studio], developing
- Web Parts [SharePoint development in Visual Studio], creating
- Web Parts [SharePoint development in Visual Studio], designing
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 9bdeb3397c3c958912010af9f822b48a66add8e6
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122123287"
---
# <a name="walkthrough-create-a-web-part-for-sharepoint"></a>Adım adım kılavuz: SharePoint için web bölümü oluşturma

Web Bölümleri tarayıcı kullanarak kullanıcıların site sayfalarının içeriğini, görünümünü ve SharePoint doğrudan değiştirmesini sağlar. Bu kılavuzda, Visual Studio 2010'da **Web Bölümü** öğe şablonunu kullanarak bir Web Bölümü oluşturma açıklanır.

Web Bölümü, bir veri kılavuzunda çalışanları görüntüler. Kullanıcı, çalışan verilerini içeren dosyanın konumunu belirtir. Kullanıcı ayrıca yönetici olan çalışanların yalnızca listede görünmesi için veri kılavuzuna filtre uygulama da sağlar.

Bu izlenecek yol aşağıdaki görevleri gösterir:

- Web Bölümü öğe şablonunu kullanarak Visual Studio **Bölümü** oluşturma.

- Web Bölümü kullanıcısı tarafından ayarlan bir özellik oluşturma. Bu özellik, çalışan veri dosyasının konumunu belirtir.

- Web Bölümü denetim koleksiyonuna denetimler ekleyerek bir Web Bölümünde içerik işleme.

- İşlenen Web parçasının fiiller  menüsünde görünen fiil olarak adlandırılan yeni bir menü öğesi oluşturma. Fiiller, kullanıcının Web Bölümünde görünen verileri değiştirmesini sağlar.

- Web Bölümünü SharePoint.

    > [!NOTE]
    > Bilgisayarınız, aşağıdaki yönergelerde yer alan Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. Daha fazla bilgi için [bkz. IDE'Visual Studio kişiselleştirme.](../ide/personalizing-the-visual-studio-ide.md)

## <a name="prerequisites"></a>Önkoşullar

- Microsoft Windows ve SharePoint.

- Visual Studio 2017 veya Azure DevOps Services.

## <a name="create-an-empty-sharepoint-project"></a>Boş bir SharePoint oluşturma

İlk olarak boş bir SharePoint oluşturun. Daha sonra, Web Bölümü öğe şablonunu kullanarak projeye bir **Web Bölümü** eksersiniz.

1. Başlangıç [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] olarak Yönetici Olarak Çalıştır **seçeneğini** kullanın.

2. Erkek çubuğunda Dosya Yeni **Dosya'Project.**  >    >  

3. Yeni **Project** iletişim kutusunda, **SharePoint** dil altındaki yeni düğüm düğümünü genişletin ve **ardından 2010 düğümünü** seçin.

4. Şablonlar **bölmesinde,** **2010'SharePoint 2010'Project** seçin ve ardından Tamam **düğmesini** seçin.

     SharePoint **Özelleştirme Sihirbazı** görüntülenir. Bu sihirbaz, projede hata ayıklamak için kullanabileceğiniz siteyi ve çözümün güven düzeyini seçmenizi sağlar.

5. Grup çözümü **olarak dağıt seçeneğini belirleyin** ve  ardından sitenin varsayılan yerel çözümünü kabul etmek için Son SharePoint seçin.

## <a name="add-a-web-part-to-the-project"></a>Projeye web bölümü ekleme

Projeye **bir Web** Bölümü öğesi ekleyin. **Web Bölümü öğesi,** Web Bölümü kod dosyasını ekler. Daha sonra, Web Bölümü'nin içeriğini işlemek için Web Bölümü kod dosyasına kod eksersiniz.

1. Menü çubuğunda Yeni Öğe **Ekle'Project**  >  **seçin.**

2. Yeni **Öğe Ekle iletişim** kutusundaki  Yüklü Şablonlar bölmesinde, SharePoint  düğümünü genişletin ve ardından **2010 düğümünü** seçin.

3. Uygulama şablonları SharePoint Web Bölümü şablonunu **ve** ardından Ekle **düğmesini** seçin.

     Web **Bölümü öğesi,** öğesinde **Çözüm Gezgini.**

## <a name="rendering-content-in-the-web-part"></a>Web bölümünde içerik işleme

Web Bölümü sınıfının denetim koleksiyonuna ekleyerek, Web Bölümünde hangi denetimlerin görünmesini istediğinizi belirtabilirsiniz.

1. Bu **Çözüm Gezgini** *WebPart1.vb* (Visual Basic) veya *WebPart1.cs* (C# içinde) açın.

     Web Bölümü kod dosyası Kod Düzenleyicisi'nde açılır.

2. Aşağıdaki yönergeleri Web Bölümü kod dosyasının en üstüne ekleyin.

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs" id="Snippet1":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb" id="Snippet1":::

3. Aşağıdaki kodu `WebPart1` sınıfına ekleyin. Bu kod aşağıdaki alanları bildirmektedir:

   - Web Bölümünde çalışanları görüntülemek için bir veri kılavuzu.

   - Denetimde görüntülenen ve veri kılavuzlarını filtrelemek için kullanılan metin.

   - Veri kılavuzu verileri görüntüleyenene kadar hata görüntüleyen bir etiket.

   - Çalışan veri dosyasının yolunu içeren bir dize.

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs" id="Snippet2":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb" id="Snippet2":::

4. Aşağıdaki kodu `WebPart1` sınıfına ekleyin. Bu kod, Web Bölümü'ne `DataFilePath` adlı özel bir özellik ekler. Özel özellik, kullanıcı tarafından bir SharePoint özelliğidir. Bu özellik, veri kılavuzu doldurmak için kullanılan bir XML veri dosyasının konumunu alır ve ayarlar.

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs" id="Snippet3":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb" id="Snippet3":::

5. `CreateChildControls` yöntemini aşağıdaki kodla değiştirin. Bu kod aşağıdaki görevleri gerçekleştirir:

   - Önceki adımda bildirilen veri kılavuzu ve etiketi ekler.

   - Veri kılavuzlarını çalışan verilerini içeren bir XML dosyasına bağlar.

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs" id="Snippet4":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb" id="Snippet4":::

6. Sınıfına aşağıdaki yöntemi `WebPart1` ekleyin. Bu kod aşağıdaki görevleri gerçekleştirir:

   - İşlenen Web parçasının Web Bölümü fiiller menüsünde görünen bir fiil oluşturur.

   - Kullanıcı fiil menüsünde fiili seçtiklerinde ortaya çıkar olayı işler. Bu kod, veri kılavuzunda görünen çalışanların listesini filtreler.

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs" id="Snippet5":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb" id="Snippet5":::

## <a name="test-the-web-part"></a>Web bölümünü test edin

Projeyi çalıştırdıktan sonra SharePoint açılır. Web Bölümü, Web Bölümü Galerisi'ne otomatik olarak SharePoint. Web Bölümünü herhangi bir Web Bölümü sayfasına eklemek için kullanabilirsiniz.

1. Aşağıdaki XML dosyasını bir Not Defteri yapıştırın. Bu XML dosyası, Web Bölümünde görünecek örnek verileri içerir.

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
        <employees xmlns="http://schemas.microsoft.com/vsto/samples">
           <employee>
               <name>David Hamilton</name>
               <hireDate>2001-05-11</hireDate>
               <title>Sales Associate</title>
           </employee>
           <employee>
               <name>Karina Leal</name>
               <hireDate>1999-04-01</hireDate>
               <title>Manager</title>
           </employee>
           <employee>
               <name>Nancy Davolio</name>
               <hireDate>1992-05-01</hireDate>
               <title>Sales Associate</title>
           </employee>
           <employee>
               <name>Steven Buchanan</name>
               <hireDate>1955-03-04</hireDate>
               <title>Manager</title>
           </employee>
           <employee>
               <name>Suyama Michael</name>
               <hireDate>1963-07-02</hireDate>
               <title>Sales Associate</title>
           </employee>
        </employees>
    ```

2. Bu Not Defteri menü çubuğunda Dosya Farklı **Kaydet'i**  >  **seçin.**

3. Farklı **Kaydet iletişim** kutusundaki Farklı kaydet türü **listesinde Tüm** Dosyalar'ı **seçin.**

4. Dosya **adı kutusuna** **data.xml.**

5. Klasörlere Gözat düğmesini **kullanarak herhangi bir klasörü** seçin ve ardından Kaydet **düğmesini** seçin.

6. Bu Visual Studio **F5 anahtarını** seçin.

     SharePoint sitesi açılır.

7. Site Eylemleri **menüsünde Diğer** Seçenekler'i **seçin.**

8. Oluştur **sayfasında** Web Bölümü Sayfası **türünü ve** ardından Oluştur **düğmesini** seçin.

9. Yeni **Web Bölümü Sayfası sayfasında,** sayfaya **SampleWebPartPage.aspx** adını ve ardından Oluştur **düğmesini** seçin.

     Web Bölümü sayfası görüntülenir.

10. Web Bölümü sayfasında herhangi bir bölgeyi seçin.

11. Sayfanın üst kısmında Ekle sekmesini **ve** ardından Web Bölümü **düğmesini** seçin.

12. Kategoriler **bölmesinde** Özel klasörü  seçin, **WebPart1** Web Bölümü'ni ve ardından Ekle **düğmesini** seçin.

     Web Bölümü sayfada görünür.

## <a name="test-the-custom-property"></a>Özel özelliği test etmek

Web Bölümünde görüntülenen veri kılavuzlarını doldurmak için, her çalışanla ilgili verileri içeren XML dosyasının yolunu belirtin.

1. Web Bölümü'nin sağ tarafında görüntülenen oku seçin ve sonra görüntülenen **menüden Web** Bölümünü Düzenle'yi seçin.

     Sayfanın sağ tarafında Web Bölümü özelliklerini içeren bir bölme görüntülenir.

2. Bölmede Çeşitli **düğümünü** genişletin, daha önce oluşturduğunuz XML dosyasının yolunu girin, Uygula  düğmesini seçin ve ardından Tamam **düğmesini** seçin.

     Web Bölümünde çalışanların listesinin görüntülendiğinden emin olmak.

## <a name="test-the-web-part-verb"></a>Web bölümü fiilini test edin

Web Bölümü fiilleri menüsünde görüntülenen bir öğeyi seçerek yönetici olan çalışanları göster ve gizle.

1. Web Bölümü'nin sağ tarafında görüntülenen oku seçin ve ardından görüntülenen **menüden Yalnızca** Yöneticileri Göster'i seçin.

     Yalnızca yönetici olan çalışanlar Web Bölümünde görünür.

2. Oku yeniden seçin ve ardından görüntülenen **menüden Tüm Çalışanları** Göster'i seçin.

     Tüm çalışanlar Web Bölümünde görünür.

## <a name="see-also"></a>Ayrıca bkz.

[SharePoint için web bölümleri oluşturma](../sharepoint/creating-web-parts-for-sharepoint.md) 
 [Nasıl SharePoint web bölümü oluşturma](../sharepoint/how-to-create-a-sharepoint-web-part.md) 
 [Nasıl kullanılır: Tasarımcı SharePoint web bölümü oluşturma](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md) 
 [Adım adım kılavuz: Tasarımcı kullanarak SharePoint web bölümü oluşturma](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)
