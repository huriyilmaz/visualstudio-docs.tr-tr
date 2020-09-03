---
title: Sunucu Gezgini kullanarak SharePoint bağlantılarına göz atma | Microsoft Docs
ms.date: 02/02/2017
ms.topic: overview
f1_keywords:
- VS.SharePointTools.SharePointExplorer.SharePointConnection
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, browsing SharePoint sites
- SharePoint development in Visual Studio, SharePoint Connections
- SharePoint Connections [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: baf580ace98ab14032de1e9a3edf18af2b2cfee8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86016347"
---
# <a name="browse-sharepoint-connections-by-using-server-explorer"></a>Sunucu Gezgini kullanarak SharePoint bağlantılarına gözatın
  Artık **Sunucu Gezgini**'de yerel SharePoint bağlantılarına gözatabiliyor olabilirsiniz. Bu tekniği kullanarak, sisteminizdeki bir SharePoint sitesinin bileşenlerine gidebilirsiniz. Liste tanımları ve içerik türleri gibi SharePoint site bileşenleri, **Sunucu Gezgini**ağaç görünümünde **SharePoint bağlantıları** adlı bir düğümde görüntülenir. **Sunucu Gezgini**görüntülemek için, menü çubuğunda, Sunucu Gezgini **görüntüle**' yi seçin  >  **Server Explorer**. SharePoint site bileşenlerini görüntülemenin yanı sıra, öğeleri kaldırabilir, özelliklerini görüntüleyebilir veya kısayol menüsündeki komutları kullanarak ağaç görünümünü yenileyebilirsiniz.

> [!IMPORTANT]
> Bir SharePoint sitesine gözatabilmeniz için SharePoint site koleksiyonunun yöneticisi olmanız ve Visual Studio 'Yu yerel bilgisayarın yöneticisi olarak çalıştırıyor olmanız gerekir. Aksi takdirde, site **Sunucu Gezgini**görüntülenir, ancak düğümünü genişletemez. Site koleksiyonunun Yöneticisi olup olmadığını doğrulamak için, siteyi bir Web tarayıcısında açın, site **eylemleri** menüsünü açın, **Site izinleri**' ni seçin ve ardından **izinler: ekip sitesi** sayfasında, Şeritteki **Yönet** grubundan **site koleksiyonu yöneticileri** komutunu seçin. Bir site koleksiyonu yöneticisiyseniz adınız metin kutusunda görünür. **Site koleksiyonu yöneticileri** komutu Şeritteki Yönet grubunda görünmezse, site koleksiyonu için yönetici değilsiniz ve site yöneticisinden uygun izinleri edinmeniz gerekir.

## <a name="server-explorer-nodes"></a>Sunucu Gezgini düğümleri
 SharePoint sitesinin her bileşeni, **SharePoint bağlantıları**altındaki **Sunucu Gezgini** ağaç görünümündeki bir düğüm tarafından temsil edilir. Örneğin, varsayılan SharePoint siteleri, SharePoint sitesinin **tartışmalar** sayfasında görüntülenen bir tartışma türünü temsil eden tartışma adlı bir içerik türü içerir. Tartışma içerik türü çeşitli alanları içerir. **Sunucu Gezgini**içinde bu alanları görüntülemek Için **ContentTypes** düğümünü ve ardından **Discussion** düğümünü genişletin. Altında gövde, tartışma konusu ve başlık gibi çeşitli alan düğümleri bulunur.

## <a name="node-shortcut-menu-commands"></a>Düğüm kısayol menü komutları
 Her düğümün, düğüme sağ tıklayıp ve ardından **SHIFT** + **F10** tuşlarını seçerek erişebileceğiniz bir kısayol menüsü vardır. Düğüm komutları şunları içerebilir:

|Komut adı|Description|
|------------------|-----------------|
|Yenile|Ağaç görünümünü, düğümün en son görüntülenmesinden bu yana oluşmuş olabilecek değişiklikleri yansıtacak şekilde güncelleştirir.|
|Sil|Seçili düğümü ağaç görünümünden kaldırır. **Note:**  Bu komut yalnızca **SharePoint** bağlantıları düğümü altında listelenen SharePoint bağlantılarında etkindir.|
|Özellikler|**Özellikler** penceresinde seçili düğüm için kullanılabilen özellikleri görüntüler. Özelliklerin hepsi salt okunurdur ve her düğümde ilişkili özellikler yoktur.|
|Bağlantı ekle|Gezinmek istediğiniz bir SharePoint sitesi belirtmenizi sağlar. **SharePoint bağlantıları** düğümünde ve alt site düğümlerinde kullanılabilir.|
|Tarayıcıda görüntüle|Seçili listeyi Web tarayıcısında görüntüler. Bu komut, listelerde **ve kitaplıklarda**bulunan **listeler** düğümü altındaki bazı listelerde kullanılabilir.|

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Nasıl yapılır: SharePoint bağlantıları ekleme veya kaldırma](../sharepoint/how-to-add-or-remove-sharepoint-connections.md)|**Sunucu Gezgini**yeni bir SharePoint sitesini **SharePoint bağlantıları** düğümüne eklemek için gereken adımları açıklar.|

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint çözümleri geliştirme](../sharepoint/developing-sharepoint-solutions.md)
