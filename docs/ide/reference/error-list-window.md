---
title: Hata Listesi Penceresi
description: Hata Listesi penceresini ve bu pencereyi, görüntüle ilgili hataları çözümlemeyle ilgili görevleri gerçekleştirmek için nasıl kullanabileceğiniz hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Task List
- build errors
- Error List window
- errors [Visual Studio], Error List window
ms.assetid: b7f6d45a-733b-4ad8-bc2f-737a37509e56
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 3690bdcfd80593599d792c2091583e95fdc513b6
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122144008"
---
# <a name="error-list-window"></a>Hata Listesi Penceresi

> [!NOTE]
> Hata **Listesi belirli** bir hata iletisiyle ilgili bilgileri görüntüler. Çıkış penceresinden hata numarasını veya hata dizesi metnini **kopyaabilirsiniz.** Çıkış penceresini görüntülemek **için** **Ctrl** Alt O + **tuşlarına** + **basın.** Bkz. [Çıkış penceresi.](../../ide/reference/output-window.md)

Hata **Listesi penceresi** aşağıdaki görevleri gerçekleştirmenizi sağlar:

- Kod yazma sırasında üretilen hataları, uyarıları ve iletileri görüntüleme.

- IntelliSense tarafından not alan söz dizimi hatalarını bulma.

- Dağıtım hatalarını, bazı Statik Analiz hatalarını ve Şablon ilkelerine uygulama sırasında Enterprise hataları bulun.

- Sorunun oluştuğu dosyayı açmak için herhangi bir hata iletisi girdisini çift tıklatın ve hata konuma inin.

- Hangi girdilerin görüntülenmiyor ve her giriş için hangi bilgi sütunlarının görüntüleniyor olduğunu filtrele.

- Belirli terimler için arama ve arama kapsamını yalnızca geçerli proje veya belge olarak seçin.

Hata **Listesi'ni görüntülemek için** Hata Listesini **Görüntüle'yi**  >  **seçin** veya **Ctrl** E + **\\** + **tuşlarına basın.**

Farklı bilgi düzeylerini **görmek için** **Hatalar,** Uyarılar **ve** İletiler sekmelerini seçebilirsiniz.

Listeyi sıralamak için herhangi bir sütun başlığına tıklayın. Yeniden ek sütuna göre sıralamak için Shift tuşunu basılı **tutun** ve başka bir sütun başlığına tıklayın. Görüntülenen ve gizlenen sütunları seçmek için kısayol **menüsünden Sütunları Göster'i** seçin. Sütunların görüntülenme sıralarını değiştirmek için sütun üst bilgilerini sola veya sağa sürükleyin.

## <a name="error-list-filters"></a>Hata Listesi Filtreleri

İki açılan kutu içinde biri araç çubuğunun sağ tarafında, biri de araç çubuğunun sol tarafında olmak için iki tür filtre vardır. Araç çubuğunun sol tarafındaki açılan liste, kullanmak üzere kod dosyaları kümesi belirtir ( Tüm **Çözüm,** **Açık** Belgeler, Geçerli **Project**, **Geçerli Belge**).

Hata gruplarını analiz etmek ve bu gruplara göre hareket etmek için arama kapsamını kısıtabilirsiniz. Örneğin, bir projenin derlemesini engelleyen temel hatalara odaklanmak istiyor olabilir. Bu seçeneklerin bazıları şunlardır:

1. **Açık Belgeler:** Açık belgeler için hataları, uyarıları ve iletileri gösterir.

2. **Geçerli Project:** Düzenleyici'de o anda seçili olan belgenin projesinde veya içinde seçilen projeden gelen **hataları,** uyarıları ve **iletileri Çözüm Gezgini.**

    > [!NOTE]
    > Şu anda seçili olan belgenin projesi, içinde seçilen projeden farklı ise, filtrelenmiş hata, uyarı ve ileti **listesi Çözüm Gezgini.**

3. **Geçerli Belge:** Düzenleyicide veya düzenleyicide seçili olan belge için **hataları,** uyarıları ve **iletileri Çözüm Gezgini.**

Arama sonuçlarına şu anda bir filtre uygulanmışsa, filtrenin adı Hata Listesi **başlık çubuğunda** görünür. Ardından **Hatalar,** **Uyarılar** **ve** İletiler düğmeleri, toplam öğe sayısıyla birlikte filtrelenmiş öğe sayısını görüntüler. Örneğin, düğmeler "x of y Errors" ifadesini gösterir. Filtre uygulanmazsa başlık çubuğunda yalnızca "Hata Listesi" yer alır.

Araç çubuğunun sağ tarafındaki liste, derleme hatalarını (derleme işlemi sonucunda oluşan hatalar) veya IntelliSense'den (derlemeyi çalıştırmadan önce algılanan hatalar) veya her ikisini birden göstermeyi belirtir.

## <a name="search"></a>Arayın

Hata **listesinde belirli hataları** bulmak için Hata  Listesi araç çubuğunun sağ tarafındaki Hata Listesini Ara metin kutusunu kullanın. Hata listesinde herhangi bir görünür sütunda arama yapmak için arama da ekleyebilirsiniz ve arama sonuçları her zaman sorgu veya uygulanan filtre yerine sıralama önceliğini içeren sütuna göre sıralanmış olur. Odak Hata **Listesindeyken Esc** tuşuna basın, arama terimini ve filtrelenmiş arama sonuçlarını temizebilirsiniz. Ayrıca, metin kutusunun sağ tarafındaki **X** tarak da bunu temizebilirsiniz.

## <a name="save"></a>Kaydet

Hata listesini kopyalayıp bir dosyaya kaydedebilirsiniz. Kopyalamak istediğiniz hataları seçin ve seçime sağ tıklayın ve bağlam menüsünde Kopyala'yı **seçin.** Ardından hataları bir dosyaya yapıştırabilirsiniz. Hataları bir elektronik tabloda Excel alanları farklı sütunlar olarak görünür.

## <a name="ui-element-list"></a>UI Öğe Listesi

Önem Derecesi

Farklı Hata Listesi **girdisi türlerini görüntüler** (**Hata** **,** İleti , **Uyarı**, **Uyarı (etkin)**, **Uyarı (etkin değil)**.

Kod

Hata kodunu görüntüler.

Açıklama

Girişin metnini görüntüler.

Project

Geçerli projenin adını görüntüler.

Dosya

Dosya adını görüntüler.

Çizgi

Sorunun oluştuğu satırı görüntüler.
