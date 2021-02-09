---
title: 'Nasıl yapılır: eşlenmiş klasör ekleme ve kaldırma | Microsoft Docs'
description: Eşlenen klasörleri SharePoint 'teki bir projeye ekleyin ve kaldırın.  Eşlenen bir klasörün dağıtım konumunu değiştirin. Eşlenen klasörleri yeniden adlandırın veya kaldırın.
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
ms.workload:
- office
ms.openlocfilehash: e6771482925a935d1b6424412d4176db5e9ad6c6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99923476"
---
# <a name="how-to-add-and-remove-mapped-folders"></a>Nasıl yapılır: eşlenmiş klasörler ekleme ve kaldırma
  SharePoint 'te resim ve düzen gibi yaygın olarak kullanılan bazı klasörler, dosya hiyerarşisinde derin bir şekilde katıştırılır. Bu klasörleri daha kolay erişmek için bir SharePoint projesiyle eşleyebilirsiniz. Eşlenen klasörler SharePoint projesinde SharePoint Server yüklemesinde dosyaların fiziksel konumuna karşılık gelen klasörlerdir.

 Bir SharePoint uygulaması dağıttığınızda, eşlenmiş klasörün içeriği ve tüm alt klasörleri, SharePoint klasör ağacındaki belirtilen konumda SharePoint çalıştıran sunucuya çözüm paketi (. wsp) tarafından kopyalanır. Bu konum, eşlenen klasör için ayarlanan **dağıtım konumu** özelliği tarafından belirlenir. Eşlenen klasördeki tüm alt klasörler, eşlenmiş klasörün **dağıtım konumuyla** ilişkilidir. Eşlenen klasörün adı değil **dağıtım konumu** özelliğinin, öğelerin nereye dağıtılacağını belirlediğini unutmayın.
Proje için menü çubuğundaki komutları veya kısayol menüsünü kullanarak, eşlenen klasörleri bir projeye ekleyebilirsiniz. En sık kullanılan eşlenmiş klasörleri eklemek için **SharePoint "görüntüleri" eşlenmiş klasörünü** ve **SharePoint "düzenleri" klasörü Ekle** komutlarını kullanabilirsiniz. Kısayol menüsünde **SharePoint eşlenmiş klasörü Ekle** komutunu kullanarak ve sonra **SharePoint eşlenmiş klasör ekle** iletişim kutusunda klasörleri belirterek, diğer kullanılabilir SharePoint klasörlerinin herhangi birini projenize eşleyebilirsiniz.

## <a name="add-mapped-folders-to-a-project"></a>Bir projeye eşlenmiş klasörler ekleme
 Aşağıdaki yordamda, iki eşlenmiş klasörün bir Visual Web Bölümü projesine nasıl ekleneceği açıklanmaktadır. Başlamak için bir Visual Web Bölümü projesi oluşturun.

#### <a name="to-add-mapped-folders-to-a-project"></a>Eşlenen klasörleri bir projeye eklemek için

1. Menü çubuğunda **Dosya**  >  **Yeni**  >  **Proje**' yi seçin.

2. **Yeni proje** iletişim kutusunda, **Visual Basic** veya **Visual C#** düğümünü genişletin, **Office/SharePoint** düğümünü genişletin ve ardından **SharePoint çözümleri** düğümünü seçin.

3. Proje şablonları listesinde, **SharePoint 2013 Visual Web Bölümü** şablonunu seçin.

4. **Ad** kutusuna **TestProject1** girin ve sonra **Tamam** düğmesini seçin.

5. **SharePoint Özelleştirme Sihirbazı**'nda, varsayılan ayarları sürdürmek için **son** düğmesini seçin.

6. **Çözüm Gezgini**, proje düğümünü seçin ve ardından menü çubuğunda, **Proje**  >  **SharePoint "resimleri" eşlenmiş klasör ekle**' yi seçin.

     Projenizde **resim** adında bir klasör görünür ve TestProject1 adlı bir alt klasör içerir. Bu eşlenmiş klasör, Visual Web Bölümü projesinin görüntülerini içerir.

7. **Çözüm Gezgini**, proje düğümünü seçin ve ardından menü çubuğunda, SharePoint eşlenmiş klasör Ekle   >  iletişim kutusunu göstermek için proje **SharePoint eşlenmiş klasör ekle** ' yi  seçin.

8. Eşleme için kullanılabilen klasörlerin ağaç görünümünde **kaynaklar** klasörünü seçin ve **Tamam** düğmesini seçin.

     Projenizde **kaynaklar** adlı bir klasör görüntülenir. Bu klasör, dize kaynak dosyaları gibi öğeleri saklayabilir. Alt klasörler eşlenmiş bir klasörün içeriğini düzenlemek için yararlı olabilir, ancak **SharePoint eşlenmiş klasör ekle** komutunu kullanarak eşlenmiş bir klasör eklediğinizde otomatik olarak oluşturulmazlar. Bir alt klasör eklemek için **kaynaklar** klasörünü seçin ve ardından menü çubuğunda **Proje**  >  **Yeni klasör**' ü seçin.

## <a name="change-the-deployment-location-of-a-mapped-folder"></a>Eşlenen bir klasörün dağıtım konumunu değiştirme
 Varsayılan olarak, eşlenmiş klasörler, belirtecin başvurduğu SharePoint kök yükleme yoluna göre belirli konumlara eklenir \<SharePointRoot> . Ancak, eşlenmiş klasörün **dağıtım konumu** özelliğini değiştirerek bu konumu değiştirebilirsiniz. Eşlenen her klasörün kendi **dağıtım konumu** özelliği vardır.

#### <a name="to-change-the-deployment-location-of-a-mapped-folder"></a>Eşlenmiş bir klasörün dağıtım konumunu değiştirmek için

1. Daha önce oluşturduğunuz projede, eşlenmiş bir klasör seçin.

2. **Özellikler** penceresinde **dağıtım konumu** özelliğinde üç nokta (![ASP.net Mobile Designer elips](../sharepoint/media/mwellipsis.gif "ASP.NET Mobile Designer elips")) düğmesini seçin.

3. **SharePoint eşlenmiş klasörü Ekle** iletişim kutusunda, eşlenmiş klasörün işaret olmasını istediğiniz klasöre gidin.

4. Düğümünü seçin ve ardından **Tamam** düğmesini seçin.

## <a name="rename-or-remove-mapped-folders"></a>Eşlenen klasörleri yeniden adlandırma veya kaldırma

#### <a name="to-rename-or-remove-a-mapped-folder"></a>Eşlenmiş bir klasörü yeniden adlandırmak veya kaldırmak için

1. Daha önce oluşturduğunuz projede, eşlenmiş bir klasör seçin.

2. Eşlenen klasörü yeniden adlandırmak için, kısayol menüsünü açın, **Yeniden Adlandır**' ı seçin, yeni adı girin ve Enter tuşunu seçin.

     Alternatif olarak, yeniden adlandırmak istediğiniz eşlenmiş klasörü seçebilir, **Özellikler** penceresini açabilir ve ardından **klasör adı** özelliğinin değerini yeni ad olarak ayarlayabilirsiniz.

3. Eşlenen bir klasörü projeden kaldırmak için, onun kısayol menüsünü açın, **Sil**' i seçin ve ardından Iletişim kutusunda **Tamam** düğmesini seçerek kaldırma işlemini onaylayın.

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint çözümleri geliştirme](../sharepoint/developing-sharepoint-solutions.md)
