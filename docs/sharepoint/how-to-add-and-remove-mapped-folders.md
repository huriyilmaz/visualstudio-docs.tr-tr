---
title: 'Nasıl yapılır: eşlenmiş klasör ekleme ve kaldırma | Microsoft Docs'
description: Eşlenen klasörleri SharePoint bir projeye ekleyin ve kaldırın.  Eşlenen bir klasörün dağıtım konumunu değiştirin. Eşlenen klasörleri yeniden adlandırın veya kaldırın.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.Project.MappedFolder
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, mapped folders
- mapped folders [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: b632b9e261b2420d932be71e0cbc1216ae94b6ef
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122136111"
---
# <a name="how-to-add-and-remove-mapped-folders"></a>Nasıl yapılır: eşlenmiş klasörler ekleme ve kaldırma

  resim ve düzen gibi SharePoint yaygın olarak kullanılan bazı klasörler dosya hiyerarşisinde derin bir şekilde katıştırılır. bu klasörleri daha kolay erişmek için bir SharePoint projesi ile eşleyebilirsiniz. eşlenen klasörler, SharePoint sunucusu yüklemesinde dosyaların fiziksel konumuna karşılık gelen SharePoint projesindeki klasörlerdir.

 bir SharePoint uygulaması dağıttığınızda, eşlenmiş klasörün ve tüm alt klasörlerinin içeriği, SharePoint klasör ağacındaki belirtilen konumda SharePoint çalıştıran sunucuya çözüm paketi (. wsp) tarafından kopyalanır. Bu konum, eşlenen klasör için ayarlanan **dağıtım konumu** özelliği tarafından belirlenir. Eşlenen klasördeki tüm alt klasörler, eşlenmiş klasörün **dağıtım konumuyla** ilişkilidir. Eşlenen klasörün adı değil **dağıtım konumu** özelliğinin, öğelerin nereye dağıtılacağını belirlediğini unutmayın.
Proje için menü çubuğundaki komutları veya kısayol menüsünü kullanarak, eşlenen klasörleri bir projeye ekleyebilirsiniz. en sık kullanılan eşlenmiş klasörleri eklemek için, **SharePoint "görüntüleri" eşlenmiş klasörünü** ve **SharePoint "düzenleri" klasör** komutlarını ekleyebilirsiniz. kısayol menüsündeki **SharePoint eşlenmiş klasör ekle** komutunu kullanarak ve ardından **SharePoint eşlenmiş klasör ekle** iletişim kutusunda klasörleri belirterek, diğer kullanılabilir SharePoint klasörlerinden herhangi birini projenize eşleyebilirsiniz.

## <a name="add-mapped-folders-to-a-project"></a>Bir projeye eşlenmiş klasörler ekleme

 Aşağıdaki yordamda, iki eşlenmiş klasörün bir Visual Web Bölümü projesine nasıl ekleneceği açıklanmaktadır. Başlamak için bir Visual Web Bölümü projesi oluşturun.

## <a name="to-add-mapped-folders-to-a-project"></a>Eşlenen klasörleri bir projeye eklemek için

1. menü çubuğunda **dosya**  >  **yeni**  >  **Project**' yi seçin.
::: moniker range="=vs-2017"
2. **yeni Project** iletişim kutusunda, **Visual Basic** ya da **Visual C#** düğümünü genişletin, **Office/SharePoint** düğümünü genişletin ve ardından **SharePoint Solutions** düğümünü seçin.

3. proje şablonları listesinde **SharePoint 2013 Visual Web bölümü** şablonunu seçin.

4. **Ad** kutusuna **TestProject1** girin ve sonra **Tamam** düğmesini seçin.
::: moniker-end
::: moniker range=">=vs-2019"
2. **yeni Project oluştur** iletişim kutusunda, yüklemiş olduğunuz SharePoint özgü sürümü için *Visual Web bölümü * SharePoint* seçin. örneğin, SharePoint 2019 yüklemesi varsa **SharePoint 2019 Visual Web bölümü** şablonunu seçin.
    [!INCLUDE[new-project-dialog-search](../sharepoint/includes/new-project-dialog-search-md.md)]

3. **Ad** kutusuna **TestProject1** girin.
4. Ardından **Oluştur** düğmesini seçin.
::: moniker-end

5. **SharePoint özelleştirme sihirbazında**, varsayılan ayarları sürdürmek için **son** düğmesini seçin.

6. **Çözüm Gezgini**, proje düğümünü seçin ve ardından menü çubuğunda, **Project**  >  **SharePoint "resimleri" eşlenmiş klasör ekle**' yi seçin.

     Projenizde **resim** adında bir klasör görünür ve TestProject1 adlı bir alt klasör içerir. Bu eşlenmiş klasör, Visual Web Bölümü projesinin görüntülerini içerir.

7. **Çözüm Gezgini**, proje düğümünü seçin ve ardından menü çubuğunda,   >  **SharePoint eşlenmiş klasör ekle** iletişim kutusunu göstermek için Project **SharePoint eşlenmiş klasör ekle** ' yi seçin.

8. Eşleme için kullanılabilen klasörlerin ağaç görünümünde **kaynaklar** klasörünü seçin ve **Tamam** düğmesini seçin.

     Projenizde **kaynaklar** adlı bir klasör görüntülenir. Bu klasör, dize kaynak dosyaları gibi öğeleri saklayabilir. alt klasörler eşlenmiş bir klasörün içeriğini düzenlemek için yararlı olabilir, ancak **SharePoint eşlenmiş klasör ekle** komutunu kullanarak eşlenmiş bir klasör eklediğinizde otomatik olarak oluşturulmazlar. bir alt klasör eklemek için **kaynaklar** klasörünü seçin ve ardından menü çubuğunda   >  **yeni klasör** Project ' yi seçin.

## <a name="change-the-deployment-location-of-a-mapped-folder"></a>Eşlenen bir klasörün dağıtım konumunu değiştirme

 varsayılan olarak, eşlenmiş klasörler, belirtecin başvurduğu SharePoint kök yükleme yoluna göre belirli konumlara eklenir \<SharePointRoot> . Ancak, eşlenmiş klasörün **dağıtım konumu** özelliğini değiştirerek bu konumu değiştirebilirsiniz. Eşlenen her klasörün kendi **dağıtım konumu** özelliği vardır.

### <a name="to-change-the-deployment-location-of-a-mapped-folder"></a>Eşlenmiş bir klasörün dağıtım konumunu değiştirmek için

1. Daha önce oluşturduğunuz projede, eşlenmiş bir klasör seçin.

2. **özellikler** penceresinde **dağıtım konumu** özelliğindeki üç nokta (![mobil tasarımcı elips ASP.NET](../sharepoint/media/mwellipsis.gif "ASP.NET Mobil tasarımcı elips")) düğmesini seçin.

3. **SharePoint eşlenmiş klasör ekle** iletişim kutusunda, eşlenen klasörün işaret olmasını istediğiniz klasöre gidin.

4. Düğümünü seçin ve ardından **Tamam** düğmesini seçin.

## <a name="rename-or-remove-mapped-folders"></a>Eşlenen klasörleri yeniden adlandırma veya kaldırma

### <a name="to-rename-or-remove-a-mapped-folder"></a>Eşlenmiş bir klasörü yeniden adlandırmak veya kaldırmak için

1. Daha önce oluşturduğunuz projede, eşlenmiş bir klasör seçin.

2. Eşlenen klasörü yeniden adlandırmak için, kısayol menüsünü açın, **Yeniden Adlandır**' ı seçin, yeni adı girin ve Enter tuşunu seçin.

     Alternatif olarak, yeniden adlandırmak istediğiniz eşlenmiş klasörü seçebilir, **Özellikler** penceresini açabilir ve ardından **klasör adı** özelliğinin değerini yeni ad olarak ayarlayabilirsiniz.

3. Eşlenen bir klasörü projeden kaldırmak için, onun kısayol menüsünü açın, **Sil**' i seçin ve ardından Iletişim kutusunda **Tamam** düğmesini seçerek kaldırma işlemini onaylayın.

## <a name="see-also"></a>Ayrıca bkz.

- [SharePoint çözümleri geliştirme](../sharepoint/developing-sharepoint-solutions.md)
