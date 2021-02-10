---
title: Çevrimdışı yardım belgeleri
description: Microsoft Yardım Görüntüleyicisi kullanarak Visual Studio ve .NET gibi çeşitli ürün ve teknolojiler için çevrimdışı yardım belgeleri yükleyip görüntüleyin.
ms.date: 11/02/2017
ms.topic: conceptual
f1_keywords:
- hv_general
helpviewer_keywords:
- Microsoft Help Viewer Help
- Help Viewer, printing a topic
- printing a topic [Help Viewer]
- Help Viewer, toolbar
- Help on Help [Help Viewer]
- Help Viewer, window components
- Help Viewer, navigating
- toolbar [Help Viewer]
ms.assetid: 74e41666-2ce8-4ac0-a0e5-3723d1e322c2
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 339d424dd0b09404fc135a119606d47cf7570be3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99944101"
---
# <a name="microsoft-help-viewer"></a>Microsoft Yardım Görüntüleyicisi

Microsoft Yardım Görüntüleyicisi kullanarak, yerel bilgisayarınızdaki çeşitli ürün ve teknolojilerin içeriğini yükleyebilir ve görüntüleyebilirsiniz. Bu ürünler Visual Studio, .NET, dil başvurusu, SQL Server ve Windows geliştirme içerir. Yardım Görüntüleyicisi şunları yapmanızı sağlar:

- Kitap olarak da adlandırılan içerik kümelerini indirin. Bu, "çevrimdışı" çalışmanız ve belgelere erişiminizin olması gerektiğinde yararlı olabilir.

- İçindekiler tablosuna göz atarak ve arama yaparak konu başlığına göre konular bulun.

- Dizinde bulunan konuları arama.

- Tam metin aramasını kullanarak bilgi bulun.

- Konuları görüntüleyin, yer işaretini ve yazdırın.

Yardım Görüntüleyicisi 'ni yüklemek için bkz. [Microsoft Yardım Görüntüleyicisi yüklemesi](../help-viewer/installation.md). Çevrimiçi değil yardım görüntüleyicisinde yardım konularını okumaya başlamak için Visual Studio 'daki **Yardım** menüsüne gidin ve Yardım Görüntüleyicisi 'nde **Yardım tercihi**  >  **Başlat**' ı seçin.

> [!TIP]
> Bir internet bağlantınızın PDF sürümünü indirileceği sırada görüntüleyebilmeniz için içeriği yerel olarak indirmenin bir başka yolu. Docs.microsoft.com üzerinde birçok belge kümesi, içindekiler tablosunun (TOC) alt kısmına bir bağlantı içerir ve bu TOC 'nin tüm makalelerini içeren bir PDF dosyasını indirir.
>
> ![Visual Studio belgeleri için PDF 'YI indirin](media/overview/download-pdf.png)

## <a name="help-viewer-tour"></a>Yardım Görüntüleyicisi turu

Gezinti sekmelerini kullanarak yüklü içerikte bilgi bulabilir, konu sekmesinde veya sekmelerde yüklü içeriği görüntüleyebilir ve **Içeriği Yönet** sekmesini kullanarak içeriği yönetebilirsiniz. Ayrıca, araç çubuğundaki düğmeleri kullanarak ek görevler gerçekleştirebilir ve pencerenin sağ alt köşesinde ek bilgiler bulabilirsiniz.

### <a name="navigation-tabs"></a>Gezinti sekmeleri

|Tab|Description|
|---|-----------|
|İçindekiler|Yüklü içeriği hiyerarşi (İçindekiler tablosu) olarak görüntüler. Görüntülenen başlıkları filtrelemek için ölçüt belirtebilirsiniz.|
|Dizin oluşturma|Dizinli terimlerin alfabetik bir listesini görüntüler. Dizinde arama yapabilir, girişleri filtrelemek için ölçütler belirtebilir ve dizin girişlerinin belirttiğiniz metni içermesini veya kullanmaya başlamasını isteyebilirsiniz.|
|Sık Kullanılanlar|**Sık Kullanılanlara Ekle** düğmesini seçerek "sık kullanılan" konuları ve bu sekmede görünen konuları seçebilirsiniz. **Geçmiş** bölümü, son zamanlarda görüntülediğiniz konuların listesini görüntüler.|
|Arayın|Kodda, kod ve konu başlıkları dahil olmak üzere her yerde şartlar araygeçirebileceğiniz bir metin kutusu sağlar.|

### <a name="view-topics"></a>Konuları görüntüle

Her konu kendi sekmesinde görünür ve aynı anda birden çok konu açabilirsiniz.

### <a name="manage-content"></a>İçeriği yönetme

İçeriği **Yönet** sekmesini kullanarak içeriği yükleyebilir, güncelleştirebilir, taşıyabilir ve silebilirsiniz. Sekmenin en üstünde, bir ağ konumundan veya bir diskten ya da URI 'den kitap yükleme yapılıp yapılmayacağını belirtmek için **yükleme kaynak** denetimini kullanabilirsiniz. **Yerel depo yolu** kutusu, kitapların yerel bilgisayarda yüklü olduğu yeri gösterir ve **Taşı** düğmesini seçerek bunları farklı bir konuma taşıyabilirsiniz.

İçerik listesi, hangi kitaplar yükleyebileceğiniz veya zaten yüklü olduğunu, bir güncelleştirmenin kullanılabilir olup olmadığını ve her kitabın ne kadar büyük olduğunu gösterir. İlgili **ekleme** veya **kaldırma** bağlantılarını seçerek ve ardından **bekleyen değişiklikler** bölmesinin altındaki **Güncelleştir** düğmesini seçerek bir veya daha fazla kitap yükleyebilir veya kaldırabilirsiniz. Zaten yüklemiş olduğunuz tüm kitaplar için güncelleştirmeler varsa, pencerenin alt kısmındaki **Şimdi indirmek için buraya tıklayın** bağlantısını seçerek bu içeriği yenileyebilirsiniz. Ayrıca, ek kitaplar yüklediğinizde güncelleştirmeler varsa, yüklenen tüm kitaplar yenilenir.

> [!NOTE]
> **Içerik yönetme** sekmesinin Işlevselliği, Yardım Görüntüleyicisi Yöneticisi bu özellikleri devre dışı bıraktığında veya kullanılabilir internet erişimi yoksa farklılık gösterebilir.

### <a name="toolbar-buttons"></a>Araç çubuğu düğmeleri

**Yardım Görüntüleyici** penceresindeki araç çubuğu aşağıdaki düğmeleri içerir:

- **İçindekiler bölümünde konuyu göster** düğmesi, **İçindekiler** sekmesindeki konunun konumunu gösterir.

- **Sık Kullanılanlara Ekle** düğmesi, etkin konuyu **Sık Kullanılanlar** sekmesine ekler.

- **Konuda bul** düğmesi etkin konudaki arama metnini vurgular.

- **Yazdır** düğmesi, etkin konunun önizlemesini yazdırır veya görüntüler.

- **Görüntüleyici seçenekleri** düğmesi, metnin ne kadar büyük göründüğünü, kaç arama sonucunun geri dönediğini, geçmişteki kaç konunun gösterileceğini ve güncelleştirmelerin çevrimiçi olup olmadığını denetlemek gibi ayarları görüntüler.

- **Içeriği Yönet** düğmesi **İçeriği Yönet** sekmesini etkin hale getirir.

- Sağ taraftaki küçük üçgen, konu sekmeleri ve **Içeriği Yönet** sekmesini içeren bir sekme listesi açılır. Etkin sekme yapmak için bir sekme adı seçebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Microsoft Yardım Görüntüleyicisi yükleme](../help-viewer/installation.md)
- [Yardım Görüntüleyicisi Yönetici Kılavuzu](../help-viewer/administrator-guide.md)
- [Yerel içerik yükleyip yönetme](../help-viewer/install-manage-local-content.md)
