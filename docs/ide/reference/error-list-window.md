---
title: Hata Listesi Penceresi
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.ErrorList
helpviewer_keywords:
- Task List
- build errors
- Error List window
- errors [Visual Studio], Error List window
ms.assetid: b7f6d45a-733b-4ad8-bc2f-737a37509e56
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8c6d925f61714c524f97a57690870229b2340d21
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75569669"
---
# <a name="error-list-window"></a>Hata Listesi Penceresi

> [!NOTE]
> **Hata Listesi,** belirli bir hata iletisi hakkındaki bilgileri görüntüler. Hata numarasını veya hata dize metnini **Çıktı** penceresinden kopyalayabilirsiniz. **Çıkış** penceresini görüntülemek için **Ctrl**+**Alt**+**O**tuşuna basın. [Bkz. Çıktı penceresi.](../../ide/reference/output-window.md)

**Hata Listesi** penceresi aşağıdaki görevleri gerçekleştirmenizi sağlar:

- Kod yazarken üretilen hataları, uyarıları ve iletileri görüntüleyin.

- IntelliSense tarafından belirtilen sözdizimi hatalarını bulun.

- Kuruluş Şablonu ilkelerini uygularken dağıtım hatalarını, belirli Statik Çözümleme hatalarını ve algılanan hataları bulun.

- Sorunun oluştuğu dosyayı açmak ve hata konumuna geçmek için herhangi bir hata iletisi girişini çift tıklatın.

- Hangi girişlerin görüntülendiğini ve her giriş için hangi bilgi sütunlarının görüntülendiğini filtreleyin.

- Yalnızca geçerli proje veya belge için belirli terimleri arayın ve aramayı kapsamını arayın.

**Hata Listesini**görüntülemek için**Hata Listesini** **Görüntüle'yi** > seçin veya **Ctrl**+**\\**+**E**tuşuna basın.

Farklı bilgi düzeylerini görmek için **Hatalar,** **Uyarılar**ve **İletiler** sekmelerini seçebilirsiniz.

Listeyi sıralamak için herhangi bir sütun üstbilgisini tıklatın. Ek bir sütuna göre yeniden sıralamak için **Shift** tuşunu basılı tutun ve başka bir sütun üstbilgisini tıklatın. Hangi sütunların görüntüleneceğini ve hangilerinin gizli olduğunu seçmek için, kısayol menüsünden **Sütunları Göster'i** seçin. Sütunların görüntülenme sırasını değiştirmek için, herhangi bir sütun üstbilgisini sola veya sağa sürükleyin.

## <a name="error-list-filters"></a>Hata Listesi Filtreleri

İki açılır kutuda, biri araç çubuğunun sağ tarafında, diğeri araç çubuğunun solunda olmak üzere iki tür filtre vardır. Araç çubuğunun sol tarafındaki açılır liste kullanılacak kod dosyaları kümesini belirtir (**Tüm Çözüm**, **Belgeleri Aç**, Güncel **Proje**, **Geçerli Belge**).

Hata gruplarını çözümlemek ve harekete almak için aramanın kapsamını kısıtlayabilirsiniz. Örneğin, projenin derlemesini engelleyen temel hatalara odaklanmak isteyebilirsiniz. Kapsam seçenekleri şunlardır:

1. **Açık Belgeler**: Açık belgeleriçin hataları, uyarıları ve iletileri göster.

2. **Geçerli Proje**: **Düzenleyici'de** veya Çözüm Gezgini'nde seçili projede şu **Solution Explorer**anda seçili belgenin projesindeki hataları, uyarıları ve iletileri göster.

    > [!NOTE]
    > Şu anda seçili belgenin projesi **Çözüm Gezgini'nde**seçilen projeden farklıysa, filtre uygulanmış hatalar, uyarılar ve iletiler listesi değişecektir.

3. **Geçerli Belge**: **Düzenleyici** veya **Çözüm Gezgini'nde**şu anda seçili belgeiçin hataları, uyarıları ve iletileri göster.

Arama sonucuna şu anda bir filtre uygulanırsa, hata **listesi** başlık çubuğunda filtrenin adı görüntülenir. **Hatalar,** **Uyarılar**ve **İletiler** düğmeleri, daha sonra toplam öğe sayısıyla birlikte gösterilen filtre uygulanmış öğe sayısını görüntüler. Örneğin, düğmeler "y Hatalarının x'ini" gösterir. Filtre uygulanmazsa, başlık çubuğunda yalnızca "Hata Listesi" yazar.

Araç çubuğunun sağ tarafındaki liste, yapıdaki (bir yapı işleminden kaynaklanan hatalar) veya IntelliSense'den (yapı çalıştırmadan önce algılanan hatalar) veya her ikisinden de hataların gösterileceğini belirtir.

## <a name="search"></a>Search

Hata **listesindeki** belirli hataları bulmak için **Hata Listesi** araç çubuğunun sağ tarafındaki Arama Hata Listesi metin kutusunu kullanın. Hata listesindeki görünür sütunlarda arama yapabilirsiniz ve arama sonuçları her zaman sorgu veya uygulanan filtre yerine sıralama önceliği olan sütuna göre sıralanır. Odak **Hata Listesindeyken** **Esc** tuşunu seçerseniz, arama terimini ve filtrelenmiş arama sonuçlarını temizleyebilirsiniz. Ayrıca, metin kutusunun sağ tarafındaki **X'i** tıklattığınızda da bunu temizleyebilirsiniz.

## <a name="save"></a>Kaydet

Hata listesini kopyalayıp bir dosyaya kaydedebilirsiniz. Kopyalamak istediğiniz hataları seçin ve seçimi sağ tıklatın, ardından bağlam menüsünde **Kopyala'yı**seçin. Daha sonra hataları bir dosyaya yapıştırabilirsiniz. Hataları bir Excel elektronik tablosuna yapıştırıyorsanız, alanlar farklı sütunlar olarak görünür.

## <a name="ui-element-list"></a>UI Öğe Listesi

Severity

Farklı **hata listesi** girişi türlerini görüntüler (**Hata**, **İleti**, **Uyarı**, **Uyarı (etkin)**, Uyarı **(etkin değil)**.

Kod

Hata kodunu görüntüler.

Açıklama

Giriş metnini görüntüler.

Project

Geçerli projenin adını görüntüler.

Dosya

Dosya adını görüntüler.

Çizgi

Sorunun oluştuğu satırı görüntüler.
