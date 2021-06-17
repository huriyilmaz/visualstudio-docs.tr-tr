---
title: 'Nasıl: Eşlenmiş Klasörler Ekleme ve Kaldırma | Microsoft Docs'
description: SharePoint'te bir projeye eşlenmiş klasörler ekleme ve kaldırma.  Eşlenen klasörün dağıtım konumunu değiştirme. Eşlenen klasörleri yeniden adlandır veya kaldır.
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
ms.openlocfilehash: a9b74ba786c9d1104fd507442d959e75afb17bf2
ms.sourcegitcommit: 1f27f33852112702ee35fbc0c02fba37899e4cf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/15/2021
ms.locfileid: "112112429"
---
# <a name="how-to-add-and-remove-mapped-folders"></a>Nasıl: Eşlenmiş klasörler ekleme ve kaldırma

  SharePoint'te Görüntüler ve Düzenler gibi yaygın olarak kullanılan bazı klasörler dosya hiyerarşisine derinden katıştırır. Daha kolay erişmek için bu klasörleri bir SharePoint projesine eşlayabilirsiniz. Eşlenmiş klasörler, SharePoint Projesi'nin SharePoint Server yüklemesinde dosyaların fiziksel konumuna karşılık gelen klasörlerdir.

 Bir SharePoint uygulaması dağıtırken, eşlenen klasörün ve tüm alt klasörlerinin içeriği çözüm paketi (.wsp) tarafından SharePoint klasör ağacında belirtilen konumda SharePoint'i çalıştıran sunucuya kopyalanır. Bu konum, **eşlenen klasör** için ayarlanmış Dağıtım Konumu özelliği tarafından belirlenir. Eşlenen klasördeki tüm alt klasörler, eşlenen **klasörün Dağıtım** Konumu ile görelidir. Öğelerin **dağıtılacağı yeri** eşlenen klasörün adı değil Dağıtım Konumu özelliğinin belirler.
Menü çubuğundaki komutları veya projenin kısayol menüsünü kullanarak bir projeye eşlenmiş klasörler ekleyebilirsiniz. En sık kullanılan eşlenmiş klasörleri eklemek için **SharePoint "Görüntüler"** Eşlenen Klasörü Ekle ve **SharePoint "Düzenleri"** klasör ekle komutlarını kullanabilirsiniz. Kısayol menüsündeki SharePoint Eşlenmiş Klasör Ekle komutunu kullanarak ve ardından **SharePoint** Eşlenmiş Klasör Ekle iletişim kutusunda klasörleri belirterek kullanılabilir diğer **SharePoint** klasörlerini projenize eşlersiniz.

## <a name="add-mapped-folders-to-a-project"></a>Projeye eşlenmiş klasörler ekleme

 Aşağıdaki yordamda, bir görsel web bölümü projesine iki eşlenmiş klasörün nasıl ekli olduğu açıkmektedir. Başlamak için bir görsel web bölümü projesi oluşturun.

## <a name="to-add-mapped-folders-to-a-project"></a>Bir projeye eşlenmiş klasörler eklemek için

1. Menü çubuğunda Dosya Yeni **Proje'yi**  >    >  **seçin.**
::: moniker range="=vs-2017"
2. Yeni **Proje iletişim kutusunda** Visual Basic  veya **Visual C#** düğümünü genişletin, **Office/SharePoint** düğümünü genişletin ve **ardından SharePoint Çözümleri düğümünü** seçin.

3. Proje şablonları listesinde **SharePoint 2013 Görsel Web Bölümü şablonunu** seçin.

4. Ad **kutusuna** **TestProject1 yazın** ve tamam **düğmesini** seçin.
::: moniker-end
::: moniker range=">=vs-2019"
2. Yeni **Proje Oluştur iletişim kutusunda,** yüklemiş olduğunu *SharePoint'in* belirli bir sürümü için SharePoint Görsel Web Bölümü *'ni seçin. Örneğin, SharePoint 2019 yüklemeniz varsa **SharePoint 2019 Visual Web Bölümü şablonunu** seçin.
    [!INCLUDE[new-project-dialog-search](../sharepoint/includes/new-project-dialog-search-md.md)]

3. Ad **kutusuna** **TestProject1 yazın**
4. Ardından Oluştur **düğmesini** seçin.
::: moniker-end

5. **SharePoint Özelleştirme Sihirbazı'nda,** varsayılan **ayarları korumak** için Son düğmesini seçin.

6. Bu **Çözüm Gezgini** proje düğümünü seçin ve ardından menü çubuğunda Proje   >  **Ekle SharePoint "Görüntüler" Eşlenen Klasörü'ne tıklayın.**

     Projeniz içinde **Images** adlı bir klasör görünür ve TestProject1 adlı bir alt klasör içerir. Eşlenen bu klasör, görsel web bölümü projesinin görüntülerini içerir.

7. Bu **Çözüm Gezgini** proje düğümünü seçin ve ardından menü çubuğunda Proje SharePoint Eşlenmiş Klasörü Ekle'yi seçen SharePoint Eşlenmiş Klasör Ekle  >   **iletişim** kutusunu açın.

8. Eşleme için kullanılabilen klasörlerin ağaç görünümünde Kaynaklar klasörünü ve **ardından** Tamam **düğmesini** seçin.

     Projeniz içinde **Kaynaklar adlı** bir klasör görünür. Bu klasör dize kaynak dosyaları gibi öğeleri depolar. Alt klasörler, eşlenen bir klasörün içeriğini düzenlemek için yararlı olabilir, ancak **SharePoint** Eşlenen Klasör Ekle komutunu kullanarak eşlenmiş bir klasör eklerken otomatik olarak oluşturulmaz. Alt klasör eklemek için Kaynaklar klasörünü **seçin** ve ardından menü çubuğunda Proje Yeni **Klasör'e**  >  **tıklayın.**

## <a name="change-the-deployment-location-of-a-mapped-folder"></a>Eşlenen klasörün dağıtım konumunu değiştirme

 Varsayılan olarak eşlenen klasörler, belirteci ifade etmek için SharePoint kök yükleme yoluna göre belirli \<SharePointRoot> konumlara eklenir. Ancak, eşlenen klasörün Dağıtım konumu **özelliğini** değiştirerek bu konumu değiştirebilirsiniz. Eşlenen her klasörün kendi Dağıtım **konumu özelliği** vardır.

### <a name="to-change-the-deployment-location-of-a-mapped-folder"></a>Eşlenen bir klasörün dağıtım konumunu değiştirmek için

1. Daha önce oluşturduğunuz projede eşlenmiş bir klasör seçin.

2. Özellikler **penceresinde** Dağıtım konumu özelliğinde üç nokta (![ASP.NET](../sharepoint/media/mwellipsis.gif "ASP.NET Mobil Tasarımcı üç nokta")Mobil Tasarımcı üç nokta ) **düğmesini** seçin.

3. **SharePoint Eşlenmiş Klasörü Ekle** iletişim kutusunda, eşlenen klasörün işaret etmek istediğiniz klasöre gidin.

4. Düğümü ve ardından Tamam **düğmesini** seçin.

## <a name="rename-or-remove-mapped-folders"></a>Eşlenen klasörleri yeniden adlandırma veya kaldırma

### <a name="to-rename-or-remove-a-mapped-folder"></a>Eşlenmiş bir klasörü yeniden adlandırmak veya kaldırmak için

1. Daha önce oluşturduğunuz projede eşlenmiş bir klasör seçin.

2. Eşlenen klasörü yeniden adlandırmak için kısayol menüsünü açın, Yeniden Adlandır'ı **seçin,** yeni adı girin ve Enter tuşuna basın.

     Alternatif olarak, yeniden adlandırmak istediğiniz eşlenmiş klasörü seçebilir,  Özellikler penceresini açabilir ve ardından  Klasör adı özelliğinin değerini yeni ad olarak ayarlayın.

3. Eşlenen bir klasörü projeden kaldırmak için kısayol menüsünü açın, Sil'i seçin ve ardından kaldırma işlemini onaylamak için iletişim kutusunda Tamam düğmesini seçin. 

## <a name="see-also"></a>Ayrıca bkz.

- [SharePoint çözümleri geliştirme](../sharepoint/developing-sharepoint-solutions.md)
