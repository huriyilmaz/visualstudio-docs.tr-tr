---
title: Site sütunu, içerik türü ve liste oluşturma SharePoint
titleSuffix: ''
description: Bu kılavuzda, özel bir site sütunu (alan), site sütununu kullanan özel içerik türü ve site sütunundaki içerik türünü kullanan SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.ListDesigner.GeneralMessageHelp
- Microsoft.VisualStudio.SharePoint.Designers.ListDesigner.ViewModels.ListViewModel.SortingAndGrouping
- VS.SharePointTools.ListDesigner.SortingGrouping
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, list definitions
- SharePoint development in Visual Studio, list instances
- SharePoint development in Visual Studio, fields
- SharePoint development in Visual Studio, content types
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: aafbee5bd508930b2b7f5f260977791d0c111c2a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122092766"
---
# <a name="walkthrough-create-a-site-column-content-type-and-list-for-sharepoint"></a>Adım adım kılavuz: Site sütunu, içerik türü ve liste oluşturma SharePoint
  Aşağıdaki yordamlar, site sütunlarının (veya SharePoint alanlarının yanı sıra site sütunlarını kullanan bir içerik türünün nasıl özel bir site sütunları) oluşturularak oluşturulacaklarını gösterir. Ayrıca yeni içerik türünü kullanan bir liste oluşturma da gösterir.

 Bu izlenecek yol aşağıdaki görevleri içerir:

- [Özel site sütunları oluşturun.](#create-custom-site-columns)

- [Özel içerik türü oluşturun.](#create-a-custom-content-type)

- [Bir liste oluşturun.](#create-a-list)

- [Uygulamayı test etmek.](#test-the-application)

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- Desteklenen Windows ve SharePoint.

- [!INCLUDE[vsprvs-current](../sharepoint/includes/vsprvs-current-md.md)]

## <a name="create-custom-site-columns"></a>Özel site sütunları oluşturma
 Bu örnek, bir hastanenin hastalarını yönetmek için bir liste oluşturur. İlk olarak, içinde bir SharePoint projesi oluşturmanız [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ve buna site sütunları eklemeniz gerekir.

#### <a name="to-create-the-project"></a>Proje oluşturmak için

1. Dosya menüsünde [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] **Yeni**   >  dosya'Project.
::: moniker range="=vs-2017"
2. Yeni **Project** iletişim **kutusunda, Visual C#** veya **Visual Basic** altında, **Office/SharePoint** düğümünü genişletin ve SharePoint **Çözümler'i seçin.**

3. Şablonlar **bölmesinde,** yüklemiş **SharePoint sürümünün Project** Boş SharePoint seçin. Örneğin, 2016 yüklemesi SharePoint **2016 - Boş** SharePoint şablonunu Project seçin.  

4. Projenin adını Clinic olarak **ve ardından** Tamam **düğmesini** seçin.

5. Hata **ayıklama için siteyi** ve güvenlik düzeyini belirtin iletişim kutusunda, yeni özel alan öğesini eklemek istediğiniz yerel SharePoint sitesinin URL'sini girin veya varsayılan konumu ( `http://<` *SystemName*) `>/)` kullanın.

6. Bu **çözüm için güven düzeyi nedir? SharePoint,** Korumalı alanlı çözüm olarak **dağıt varsayılan değerini kullanın.**

     Korumalı alan ve grup çözümleri hakkında daha fazla bilgi için bkz. [Korumalı alanlı çözümde dikkat edilmesi gerekenler.](../sharepoint/sandboxed-solution-considerations.md)

7. Son **düğmesini** seçin. Proje artık içinde **Çözüm Gezgini.**
::: moniker-end
::: moniker range=">=vs-2019"
2.  Yeni **Sürüm Oluştur Project** iletişim kutusunda, **SharePoint sürümünün Project** boş SharePoint seçin. Örneğin, 2016 yüklemesi SharePoint **2016 - Boş** SharePoint şablonunu Project seçin.
    [!INCLUDE[new-project-dialog-search](../sharepoint/includes/new-project-dialog-search-md.md)]

3. Projenin adını Clinic olarak **ve ardından** Oluştur **düğmesini** seçin.

4. Hata **ayıklama için siteyi** ve güvenlik düzeyini belirtin iletişim kutusunda, yeni özel alan öğesini eklemek istediğiniz yerel SharePoint sitesinin URL'sini girin veya varsayılan konumu ( `http://<` *SystemName*) `>/)` kullanın.

5. Bu **çözüm için güven düzeyi nedir? SharePoint,** Korumalı alanlı çözüm olarak **dağıt varsayılan değerini kullanın.**

     Korumalı alan ve grup çözümleri hakkında daha fazla bilgi için bkz. [Korumalı alanlı çözümde dikkat edilmesi gerekenler.](../sharepoint/sandboxed-solution-considerations.md)

6. Son **düğmesini** seçin. Proje artık içinde **Çözüm Gezgini.**
::: moniker-end

#### <a name="to-add-site-columns"></a>Site sütunları eklemek için

1. Yeni bir site sütunu ekleyin. Bunu yapmak için, **Çözüm Gezgini**'de Clinic projesine sağ **tıklayın** ve Ardından Yeni Öğe **Ekle'yi**  >  **seçin.**

2. Yeni Öğe **Ekle iletişim** kutusunda Site Sütunu'na **tıklayın,** adı **PatientName** olarak ve ardından Ekle **düğmesini** seçin.

3. Site sütunlarının çalışma *Elements.xml,* Tür ayarını  **Metin** olarak bırakın ve Grup ayarını Clinic Site **Sütunları** **olarak değiştirme.** Tamamlandığında, site sütununu *Elements.xml* aşağıdaki örnekteki gibi olması gerekir.

    ```xml
    <Field
         ID="{f9ba60d1-5631-41fb-b016-a38cf48eef63}"
         Name="PatientName"
         DisplayName="Patient Name"
         Type="Text"
         Required="FALSE"
         Group="Clinic Site Columns">
    </Field>
    ```

    > [!TIP]
    > Visual Studio, Site Sütunu'na büyük/küçük yazılar eklerken DisplayName'e sizin için otomatik olarak bir boşluk ekler.
    > Site Sütunu adı içinde boşluk kullanmamanız önerilir çünkü çözümü dağıtıma dağıtmayı denediğiniz zaman soruna neden SharePoint.

4. Aynı yordamı kullanarak projeye iki site sütunu daha ekleyin: **PatientID** (Type = "Integer") ve **DoctorName** (Type = "Text"). Grup değerini Clinic **Site Sütunları olarak ayarlayın.**

## <a name="create-a-custom-content-type"></a>Özel içerik türü oluşturma
 Ardından, önceki yordamda oluşturduğunuz site sütunlarını içeren Kişiler içerik türünü temel alan bir içerik türü oluşturun. Temel içerik türü, yeni içerik türünde kullanmak üzere birkaç site sütunu sağladığı için, içerik türünü mevcut içerik türüne göre temel alan bir içerik türüne göre zaman tasarrufu sekleyebilirsiniz.

#### <a name="to-create-a-custom-content-type"></a>Özel içerik türü oluşturmak için

1. Projeye bir içerik türü ekleyin. Bunu yapmak için, **Çözüm Gezgini** proje düğümünü seçin

2. Menü çubuğunda Yeni Öğe **Ekle'Project**  >  **seçin.**

3. Visual **C# veya** **Visual Basic** altında, SharePoint **düğümünü** genişletin ve **ardından 2010 düğümünü** seçin.

4. Şablonlar **bölmesinde İçerik** Türü **şablonunu seçin,** adı Patient Info olarak **ve ardından** Ekle **düğmesini** seçin.

     SharePoint **Özelleştirme Sihirbazı** açılır.

5. Bu **içerik türünün hangi** temel içerik türü listeden  devralması gerekir? listesinde, yeni içerik türünün temeli olarak Kişi'yi ve ardından Son **düğmesini** seçin.

     Bunu yapmak, daha önce tanımlandığı site sütunlarına ek olarak Kişi içerik türünde diğer yararlı olabilecek site sütunlarına erişmenizi sağlar.

6. İçerik Türü tasarımcısı görüntülendiğinde  Sütunlar sekmesinde, daha önce tanımlandığı üç site sütunlarını ekleyin: **Hasta Adı,** **Hasta Kimliği** ve **Doktor Adı.** Bu sütunları eklemek için, Görünen Ad altındaki site sütunları listesinde ilk liste kutusunu seçin ve sonra da listede her site sütununu tek tek seçin.

    > [!TIP]
    > Site sütunlarını daha hızlı seçmek için sütunun adının ilk birkaç harfini girerek listeyi filtrenin.

7. Üç özel site sütununa ek olarak, site **sütunları** listesinden Açıklamalar sitesi sütununu ekleyin.

8. Gerekli **alanları yapmak** için Hasta Adı **ve** **Hasta** Kimliği sitesi sütunlarının Gerekli onay kutusunu seçin.

9. İçerik **Türü sekmesinde,** içerik türü adının Patient Info olduğundan emin **olun** ve ardından açıklamayı Hasta bilgileri kartı **olarak ayarlayın.**

10. Grup **Adı'nda** **Clinic Content Types (Klinik** İçerik Türleri) olarak değiştirin ve diğer ayarları varsayılan değerlerinde bırakın.

11. Menü çubuğunda, Dosya Tüm **Dosyaları**  >  **Kaydet'i seçin** ve ardından İçerik Türü tasarımcısını kapatın.

## <a name="create-a-list"></a>Liste oluşturma
 Şimdi yeni içerik türünü ve site sütunlarını kullanan bir liste oluşturun.

#### <a name="to-create-a-list"></a>Liste oluşturmak için

1. Projeye bir liste ekleyin. Bunu yapmak için, **Çözüm Gezgini** proje düğümünü seçin.

2. Menü çubuğunda Yeni Öğe **Ekle'Project**  >  **seçin.**

3. Visual **C#** veya **Visual Basic** altında, **SharePoint** genişletin.

4. Şablonlar **bölmesinde Liste** şablonunu seçin, **adı** Patients olarak ve ardından Ekle **düğmesini** seçin.

5. Listeyi Varsayılan **(Özel Liste)** ayarına göre **özelleştir'i bırakın** ve ardından Son **düğmesini** seçin.

6. Liste Tasarımcısı'nda İçerik Türleri **düğmesini** seçen İçerik Türü iletişim **Ayarlar** görüntüleniyor.

7. Yeni satırı seçin, içerik **türleri listesinde** Patient Info içerik türünü seçin ve ardından Tamam **düğmesini** seçin.

     Bunu yapmak Hasta Bilgileri içerik türünden **tüm** site sütunlarını listeye ekler.

8. Aşağıdakiler dışında, listede yer alan tüm site sütunlarını silin:

    - Hasta Kimliği

    - Hasta Adı

    - Ev Telefonu

    - E-mail

    - Doktor Adı

    - Yorumlar

9. Sütun **Görünen Adı'nın** altında boş bir satır seçin, özel bir liste sütunu ekleyin ve bunu Hastane olarak **girin.** Veri türünü Tek **SatırLı Metin olarak bırakın.**

     Özel liste sütunu yalnızca bu liste için geçerlidir. Bir listeye özel liste sütunu eklerken, listeye eklenen tüm sütunlar da dahil olmak üzere yeni bir liste içerik türü oluşturulur ve varsayılan liste olarak ayarlanır.

    > [!TIP]
    > Site sütunları listesinden bir sütun seçerseniz, mevcut bir site sütunu kullanılır. Ancak, listede herhangi bir sütun seçmeden bir sütun adı değeri girersiniz, listede aynı adı içeren bir sütun mevcut olsa bile özel bir liste sütunu oluşturulur.

     İsteğe bağlı olarak, özel liste sütunu için veri türünü Tek Satırlı Metin olarak ayarlamak yerine bu sütunun veri türünü Arama olarak ayarlarsınız ve değerleri bir tablodan veya başka bir listeden alınır. Arama sütunları hakkında bilgi için bkz. [SharePoint 2010'da](/previous-versions/msp-n-p/ff798514(v=pandp.10)) İlişkileri Listele [ve Arama ve Liste İlişkileri.](/previous-versions/office/developer/sharepoint-2010/ff623048(v=office.14))

10. Hasta Kimliği **ve Hasta** Adı **kutularının** yanında Gerekli **onay kutusunu** seçin.

11. Görünümler **sekmesinde,** görünüm oluşturmak için boş bir satır seçin. Görünüm **Adı sütununu** altındaki boş bir satıra **Patient Details girin.**

     Görünümler  sekmesinde, görünüm listesinde görünmesini istediğiniz sütunları SharePoint belirtebilirsiniz.

12. Yeni **Patient Details (Hasta** Ayrıntıları) satırına tıklayın ve ardından **Set as Default (Varsayılan Olarak Ayarla) düğmesini** seçin.

     Yeni görünüm artık liste için varsayılan görünüm olur.

13. Aşağıdaki sütunları Seçili Sütunlar **listesine** aşağıdaki sırayla ekleyin:

    - Hasta Kimliği

    - Hasta Adı

    - Ev Telefonu

    - E-mail

    - Doktor Adı

    - Hastane

    - Yorumlar

14. Özellikler **listesinde** Sıralama ve  Gruplama özelliğini seçin ve ardından Üç nokta düğmesini Üç Nokta ![Simgesi](../sharepoint/media/ellipsisicon.gif "Üç Nokta Simgesi") seçerek Sıralama ve **Gruplama iletişim** kutusunu açın.

15. Sütun Adı listesinde **Hasta** **Adı'na tıklayın,** Sıralama sütununu Artan olarak ayarlanmış olduğundan emin **olun** ve ardından Tamam **düğmesini** seçin. 

## <a name="test-the-application"></a>Uygulamayı test edin
 Artık özel site sütunları, içerik türü ve liste hazır, bunları SharePoint dağıtın ve uygulamayı çalıştırarak test edin.

#### <a name="to-test-the-application"></a>Uygulamayı test etmek için

1. Menü çubuğunda Dosya Hepsini **Kaydet'i**  >  **seçin.**

2. Uygulamayı **çalıştırmak için F5** anahtarını seçin.

     Uygulama derlenmiş ve ardından özellikleri SharePoint etkinleştirilir.

3. Hızlı Gezinti çubuğunda, Hastalar listesini **görüntülemek** için Hastalar **bağlantısını** seçin.

     Listede sütun adları, içinde Görünümler sekmesine girdiğiniz **adlar ile** eşleşmeli. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]

4. Hasta **bilgileri kartı oluşturmak** için Yeni öğe ekle bağlantısını seçin.

5. Alanlara bilgi girin ve kaydet **düğmesini** seçin.

     Yeni kayıt listede görünür.

## <a name="see-also"></a>Ayrıca bkz.
- [Site sütunları, içerik türleri ve liste oluşturma SharePoint](../sharepoint/creating-site-columns-content-types-and-lists-for-sharepoint.md)
- [Yeni SharePoint geliştirme](../sharepoint/developing-sharepoint-solutions.md)
- [Nasıl: Özel Alan Türü Oluşturma](/previous-versions/office/developer/sharepoint-2010/bb862248(v=office.14))
- [İçerik Türleri](/previous-versions/office/developer/sharepoint-2010/ms479905(v=office.14))
- [Sütunlar](/previous-versions/office/developer/sharepoint-2010/ms196085(v=office.14))
