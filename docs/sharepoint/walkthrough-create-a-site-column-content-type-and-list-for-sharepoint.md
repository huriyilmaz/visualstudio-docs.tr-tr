---
title: SharePoint için site sütunu, içerik türü ve liste oluşturma
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9ce76c72bad138a5c6c40afe717aadafec02c677
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86015274"
---
# <a name="walkthrough-create-a-site-column-content-type-and-list-for-sharepoint"></a>İzlenecek yol: SharePoint için site sütunu, içerik türü ve liste oluşturma
  Aşağıdaki yordamlarda, özel SharePoint site sütunlarının — veya *alanlarının*yanı sıra site sütunlarını kullanan bir içerik türü oluşturma işlemleri gösterilmektedir. Ayrıca, yeni içerik türünü kullanan bir listenin nasıl oluşturulacağını gösterir.

 Bu izlenecek yol aşağıdaki görevleri içerir:

- [Özel site sütunları oluşturun](#create-custom-site-columns).

- [Özel bir içerik türü oluşturun](#create-a-custom-content-type).

- [Bir liste oluşturun](#create-a-list).

- [Uygulamayı test](#test-the-application)edin.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Ön koşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- Desteklenen Windows ve SharePoint sürümleri.

- [!INCLUDE[vsprvs-current](../sharepoint/includes/vsprvs-current-md.md)]

## <a name="create-custom-site-columns"></a>Özel site sütunları oluşturma
 Bu örnek, bir hastanta hastaları yönetmek için bir liste oluşturur. İlk olarak, içinde bir SharePoint projesi oluşturmanız [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ve buna aşağıdaki şekilde site sütunları eklemeniz gerekir.

#### <a name="to-create-the-project"></a>Proje oluşturmak için

1. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] **Dosya** menüsünde **Yeni**  >  **Proje**' yi seçin.
::: moniker range="=vs-2017"
2. **Yeni proje** iletişim kutusunda, **Visual C#** veya **Visual Basic**altında, **Office/SharePoint** düğümünü genişletin ve ardından **SharePoint çözümleri**' ni seçin.

3. **Şablonlar** bölmesinde, SharePoint 'in yüklü olduğu belirli bir sürümü Için **SharePoint boş projesini** seçin. Örneğin, SharePoint 2016 yüklemesi varsa **sharepoint 2016-boş proje** şablonu ' nu seçin.  

4. Projenin adını **Clinic**olarak değiştirin ve **Tamam** düğmesini seçin.

5. **Hata ayıklama için site ve güvenlik düzeyini belirtin** iletişim kutusunda, yeni özel alan öğesini eklemek Istediğiniz yerel SharePoint sitesinin URL 'sini girin veya varsayılan konumu ( `http://<` *SystemName*) kullanın `>/)` .

6. **Bu SharePoint çözümünün güven düzeyi nedir?** bölümünde, varsayılan değer dağıtımı ' nı **Korumalı çözüm olarak**kullanın.

     Korumalı ve Grup çözümleri hakkında daha fazla bilgi için bkz. [Korumalı çözüm konuları](../sharepoint/sandboxed-solution-considerations.md).

7. **Son** düğmesini seçin. Proje artık **Çözüm Gezgini**listelenmiştir.
::: moniker-end
::: moniker range=">=vs-2019"
2.  **Yeni proje oluştur** iletişim kutusunda, yüklediğiniz belirli bir SharePoint sürümü Için **SharePoint boş projesini** seçin. Örneğin, SharePoint 2016 yüklemesi varsa **sharepoint 2016-boş proje** şablonu ' nu seçin.
    [!INCLUDE[new-project-dialog-search](../sharepoint/includes/new-project-dialog-search-md.md)]

3. Projenin adını **Clinic**olarak değiştirin ve **Oluştur** düğmesini seçin.

4. **Hata ayıklama için site ve güvenlik düzeyini belirtin** iletişim kutusunda, yeni özel alan öğesini eklemek Istediğiniz yerel SharePoint sitesinin URL 'sini girin veya varsayılan konumu ( `http://<` *SystemName*) kullanın `>/)` .

5. **Bu SharePoint çözümünün güven düzeyi nedir?** bölümünde, varsayılan değer dağıtımı ' nı **Korumalı çözüm olarak**kullanın.

     Korumalı ve Grup çözümleri hakkında daha fazla bilgi için bkz. [Korumalı çözüm konuları](../sharepoint/sandboxed-solution-considerations.md).

6. **Son** düğmesini seçin. Proje artık **Çözüm Gezgini**listelenmiştir.
::: moniker-end

#### <a name="to-add-site-columns"></a>Site sütunları eklemek için

1. Yeni bir site sütunu ekleyin. Bunu yapmak için, **Çözüm Gezgini**, **Clinic** projesine sağ tıklayın ve ardından **Add**  >  **Yeni öğe**Ekle ' yi seçin.

2. **Yeni öğe Ekle** Iletişim kutusunda **site sütunu**' nı seçin, adı **haentname**olarak değiştirin ve ardından **Ekle** düğmesini seçin.

3. Site sütununun *Elements.xml* dosyasında, **tür** ayarını **metin**olarak bırakın, **Grup** ayarını **Clinic site sütunları**olarak değiştirin. Bu tamamlandığında, site sütununun *Elements.xml* dosyası aşağıdaki örnekteki gibi görünmelidir.

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
    > Site sütununun adında ortası büyük harfleri kullanırsanız, Visual Studio DisplayName 'e otomatik olarak bir boşluk ekler.
    > Çözümü SharePoint 'e dağıtmaya çalıştığınızda soruna neden olabileceğinden, site sütunu adında boşluk kullanılmaması önerilir.

4. Aynı yordamı kullanarak projeye iki site sütunu ekleyin: **Hatıd** (Type = "Integer") ve **doctorname** (Type = "Text"). Grup değerini **Clinic site sütunları**olarak ayarlayın.

## <a name="create-a-custom-content-type"></a>Özel içerik türü oluştur
 Daha sonra, bir önceki yordamda oluşturduğunuz site sütunlarını içeren kişiler içerik türüne göre — bir içerik türü oluşturun. Bir içerik türünü varolan bir içerik türüne dayandırarak, temel içerik türü yeni içerik türünde kullanılmak üzere birkaç site sütunu sağladığından zamandan tasarruf edebilirsiniz.

#### <a name="to-create-a-custom-content-type"></a>Özel bir içerik türü oluşturmak için

1. Projeye bir içerik türü ekleyin. Bunu yapmak için, **Çözüm Gezgini**' de proje düğümünü seçin

2. Menü çubuğunda, **Proje**  >  **Yeni öğe Ekle**' yi seçin.

3. **Visual C#** veya **Visual Basic**altında **SharePoint** düğümünü genişletin ve ardından **2010** düğümünü seçin.

4. **Şablonlar** bölmesinde, **içerik türü** şablonu ' nu seçin, adı **hasta Info**olarak değiştirin ve ardından **Ekle** düğmesini seçin.

     **SharePoint Özelleştirme Sihirbazı** açılır.

5. **Bu içerik türünün hangi temel içerik türünde devralması gerekir** listesinden, yeni içerik türünün temel alınacağı içerik türü olarak **iletişim** ' i seçin ve ardından **son** düğmesini seçin.

     Bunu yapmak, daha önce tanımladığınız site sütunlarına ek olarak, Iletişim içeriği türündeki diğer potansiyel faydalı site sütunlarına erişmenizi sağlar.

6. Içerik türü Tasarımcısı görüntülendikten sonra, **sütunlar** sekmesinde daha önce tanımladığınız üç site sütununu ekleyin: **hasta adı**, **hasta ID**ve **Doctor Name**. Bu sütunları eklemek için, **görünen ad**' ın altındaki site sütunları listesinde ilk liste kutusunu seçin ve ardından listedeki her bir site sütununu tek seferde seçin.

    > [!TIP]
    > Site sütunlarını daha hızlı bir şekilde seçmek için sütunun adının ilk birkaç harfini girerek listeyi filtreleyin.

7. Üç özel site sütununa ek olarak, site sütunları listesinden **Comments** site sütununu ekleyin.

8. **Hasta adı** ve **hasta kimliği** site sütunlarının gerekli alanları olması için **gerekli** onay kutusunu seçin.

9. **Içerik türü** sekmesinde, içerik türü adının **hasta Info**olduğundan emin olun ve ardından açıklamayı **hasta bilgi kartı**olarak değiştirin.

10. **Grup adını** **Clinic içerik türleriyle**değiştirin ve diğer ayarları varsayılan değerlerinde bırakın.

11. Menü çubuğunda **Dosya**  >  **Tümünü Kaydet**' i seçin ve ardından içerik türü tasarımcısını kapatın.

## <a name="create-a-list"></a>Liste Oluştur
 Şimdi yeni içerik türünü ve site sütunlarını kullanan bir liste oluşturun.

#### <a name="to-create-a-list"></a>Bir liste oluşturmak için

1. Projeye bir liste ekleyin. Bunu yapmak için, **Çözüm Gezgini**' de proje düğümünü seçin.

2. Menü çubuğunda, **Proje**  >  **Yeni öğe Ekle**' yi seçin.

3. **Visual C#** veya **Visual Basic**altında **SharePoint** düğümünü genişletin.

4. Şablonlar bölmesinde, **liste** şablonunu seçin, adı **hastalar**olarak değiştirin ve ardından **Templates** **Ekle** düğmesini seçin.

5. **Listeyi** varsayılan olarak ayarla **(özel liste)** seçeneğini belirleyin ve ardından **son** düğmesini seçin.

6. Liste tasarımcısında içerik **türleri** düğmesini seçerek **içerik türü ayarları** iletişim kutusunu görüntüleyin.

7. Yeni satırı seçin, içerik türleri listesinde **hasta bilgisi** içerik türünü seçin ve **Tamam** düğmesini seçin.

     Bunu yapmak, **hasta bilgisi** içerik türünden tüm site sütunlarını listeye ekler.

8. Listede aşağıdakiler hariç tüm site sütunlarını silin:

    - Hasta KIMLIĞI

    - Hasta adı

    - Ev Telefonu

    - Postadaki

    - Doctor Name

    - Yorumlar

9. **Sütun görünen adı**altında boş bir satır seçin, özel bir liste sütunu ekleyin ve onu **barındırsıt**olarak adlandırın. Veri türünü **tek satırlık metin**olarak bırakın.

     Özel liste sütunu yalnızca bu liste için geçerlidir. Bir listeye özel bir liste sütunu eklediğinizde, listeye eklenen tüm sütunlar dahil olmak üzere yeni bir liste içerik türü oluşturulur ve varsayılan liste olarak ayarlanır.

    > [!TIP]
    > Site sütunları listesinden bir sütun seçerseniz, var olan bir site sütunu kullanılır. Ancak, listede herhangi bir sütun seçmeden bir sütun adı değeri girerseniz, listede aynı ada sahip bir sütun zaten mevcut olsa bile özel bir liste sütunu oluşturulur.

     İsteğe bağlı olarak, özel liste sütunu için veri türünü **tek satırlık metin**olarak ayarlamak yerine, bu sütunun veri türünü arama olarak ayarlayabilirsiniz ve değerleri bir tablodan ya da başka bir listeden alınır. Arama sütunları hakkında daha fazla bilgi için bkz. [SharePoint 2010 'de Ilişkileri listeleme](/previous-versions/msp-n-p/ff798514(v=pandp.10)) ve [aramalar ve liste ilişkileri](/previous-versions/office/developer/sharepoint-2010/ff623048(v=office.14)).

10. **Hasta kimliği** ve **hasta adı** kutularının yanında, **gerekli** onay kutusunu seçin.

11. **Görünümler** sekmesinde bir görünüm oluşturmak için boş bir satır seçin. **Hasta ayrıntılarını** **Görünüm adı** sütununun altındaki boş bir satıra girin.

     **Görünümler** sekmesinde, SharePoint listesinde görünmesini istediğiniz sütunları belirtebilirsiniz.

12. Yeni **hasta ayrıntıları** satırını seçin ve ardından **Varsayılan olarak ayarla** düğmesini seçin.

     Yeni görünüm artık listenin varsayılan görünümüdür.

13. Aşağıdaki sütunları **Seçili sütunlar** listesine aşağıdaki sırayla ekleyin:

    - Hasta KIMLIĞI

    - Hasta adı

    - Ev Telefonu

    - Postadaki

    - Doctor Name

    - Hastane

    - Yorumlar

14. **Özellikler** listesinde **sıralama ve gruplama** özelliğini seçin ve ardından **sıralama ve gruplama** iletişim kutusunu göstermek Için üç nokta düğmesi ![üç nokta simgesini](../sharepoint/media/ellipsisicon.gif "Üç nokta simgesi") seçin.

15. **Sütun adı** listesinde, **hasta adı**' nı seçin, **sıralama** sütununun **artan**olarak ayarlandığından emin olun ve **Tamam** düğmesini seçin.

## <a name="test-the-application"></a>Uygulamayı test etme
 Artık özel site sütunları, içerik türü ve liste hazır hale gelmiştir, bunları SharePoint 'e dağıtın ve test etmek için uygulamayı çalıştırın.

#### <a name="to-test-the-application"></a>Uygulamayı test etmek için

1. Menü çubuğunda **Dosya**  >  **Tümünü Kaydet**' i seçin.

2. Uygulamayı çalıştırmak için **F5** tuşunu seçin.

     Uygulama derlenir ve sonra özellikleri SharePoint 'e dağıtılır ve etkinleştirilir.

3. **Hastalar** listesini göstermek Için hızlı gezinti çubuğunda **hastalar** bağlantısını seçin.

     Listedeki sütun adları, içindeki **Görünümler** sekmesinde girilenlerindekilerle eşleşmelidir [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

4. Hasta bilgi kartı oluşturmak için **Yeni öğe Ekle** bağlantısını seçin.

5. Alanlara bilgileri girin ve **Kaydet** düğmesini seçin.

     Yeni kayıt listede görüntülenir.

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint için site sütunları, içerik türleri ve listeler oluşturma](../sharepoint/creating-site-columns-content-types-and-lists-for-sharepoint.md)
- [SharePoint çözümleri geliştirme](../sharepoint/developing-sharepoint-solutions.md)
- [Nasıl yapılır: özel alan türü oluşturma](/previous-versions/office/developer/sharepoint-2010/bb862248(v=office.14))
- [İçerik türleri](/previous-versions/office/developer/sharepoint-2010/ms479905(v=office.14))
- [Sütunlar](/previous-versions/office/developer/sharepoint-2010/ms196085(v=office.14))
