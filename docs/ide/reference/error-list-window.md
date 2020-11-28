---
title: Hata Listesi Penceresi
description: Hata Listesi penceresi ve görüntülediği hataları çözmeye ilişkin görevleri gerçekleştirmek için nasıl kullanılacağı hakkında bilgi edinin.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: bf008bd7c1355f5991890ca5ab8bd999f2a8dd32
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2020
ms.locfileid: "96305438"
---
# <a name="error-list-window"></a>Hata Listesi Penceresi

> [!NOTE]
> **Hata listesi** belirli bir hata iletisiyle ilgili bilgileri görüntüler. Hata numarasını veya hata dizesi metnini **Çıkış** penceresinden kopyalayabilirsiniz. **Çıkış** penceresini göstermek için **CTRL** + **alt** + **O** tuşlarına basın. [Çıkış penceresine](../../ide/reference/output-window.md)bakın.

**Hata listesi** penceresi aşağıdaki görevleri gerçekleştirmenize olanak sağlar:

- Kodu yazarken üretilen hataları, uyarıları ve iletileri görüntüleyin.

- IntelliSense tarafından belirtilen sözdizimi hatalarını bulun.

- Dağıtım hatalarını, belirli statik analiz hatalarını ve Kurumsal Şablon İlkeleri uygulanırken algılanan hataları bulun.

- Sorunun gerçekleştiği dosyayı açmak için herhangi bir hata iletisi girişine çift tıklayın ve hata konumuna gidin.

- Hangi girişlerin görüntülendiğini ve her giriş için hangi bilgi sütunlarının göründüğünü filtreleyin.

- Belirli terimleri arayın ve aramayı yalnızca geçerli proje veya belge ile kapsamını bulun.

**Hata listesi** görüntülemek için **View**  >  **hata listesi** görüntüle ' yi seçin veya **CTRL** + **\\** + **E** tuşlarına basın.

Farklı bilgi düzeylerini görmek için **hatalar**, **Uyarılar** ve **iletiler** sekmelerini seçebilirsiniz.

Listeyi sıralamak için herhangi bir sütun başlığına tıklayın. Ek bir sütuna yeniden sıralamak için **SHIFT** tuşunu basılı tutarak başka bir sütun başlığına tıklayın. Hangi sütunların görüntülendiğini ve gizli olduğunu seçmek için kısayol menüsünde **sütunları göster** ' i seçin. Sütunların görüntülenme sırasını değiştirmek için herhangi bir sütun başlığını sola veya sağa sürükleyin.

## <a name="error-list-filters"></a>Hata Listesi filtreleri

İki açılan kutuda, biri araç çubuğunun sağ tarafında ve diğeri araç çubuğunun solunda olmak üzere iki tür filtre vardır. Araç çubuğunun sol tarafındaki açılan liste, kullanılacak kod dosyası kümesini belirtir (**tüm çözüm**, **Açık belgeler**, **geçerli proje**, **geçerli belge**).

Arama kapsamını analiz edilecek ve hata gruplarını görecek şekilde kısıtlayabilirsiniz. Örneğin, bir projenin derlenmesini engelleyen temel hatalara odaklanmak isteyebilirsiniz. Kapsam seçenekleri şunlardır:

1. **Açık** belgeler: açık belgeler için hataları, uyarıları ve iletileri göster.

2. **Geçerli proje**: **düzenleyicide** veya seçilen projede seçili olan belgenin projesinden hataları, uyarıları ve iletileri göster **Çözüm Gezgini**.

    > [!NOTE]
    > Şu anda seçili olan belgenin projesi **Çözüm Gezgini**' de seçilen projeden farklıysa, hata, uyarı ve ileti filtrelenmiş listesi değişecektir.

3. **Geçerli belge**: **düzenleyicide** veya **Çözüm Gezgini** seçili olan belge için hataları, uyarıları ve iletileri göster.

Arama sonuçlarına bir filtre uygulanmışsa, filtrenin adı **hata listesi** başlık çubuğunda görüntülenir. **Hatalar**, **Uyarılar** ve **iletiler** düğmeleri daha sonra toplam öğe sayısıyla birlikte gösterilen filtrelenmiş öğe sayısını görüntüler. Örneğin, düğmeler "x/y hata" gösterir. Hiçbir filtre uygulanmazsa, başlık çubuğu yalnızca "Hata Listesi" ifadesini belirtir.

Araç çubuğunun sağ tarafındaki liste, derlemeden hataların (bir derleme işleminden kaynaklanan hatalar) veya IntelliSense 'den (bir derleme çalıştırılmadan önce algılanan hatalar) veya her ikisiyle ait hataların gösterilip gösterilmeyeceğini belirtir.

## <a name="search"></a>Arayın

Hata listesindeki belirli hataları bulmak için **hata listesi** araç çubuğunun sağ tarafındaki **arama hata listesi** metin kutusunu kullanın. Hata listesindeki görünür bir sütunda arama yapabilirsiniz ve arama sonuçları her zaman sorgu yerine sıralama önceliği olan sütuna göre sıralanır veya filtre uygulanmış olur. Odak **hata listesi**, **ESC** tuşunu seçerseniz arama terimini ve filtrelenmiş arama sonuçlarını temizleyebilirsiniz. Ayrıca, metin kutusunun sağ tarafındaki **X** simgesini tıklatarak temizleyebilirsiniz.

## <a name="save"></a>Kaydet

Hata listesini kopyalayabilir ve bir dosyaya kaydedebilirsiniz. Kopyalamak istediğiniz hataları seçin ve seçimi sağ tıklatın, ardından bağlam menüsünde **Kopyala**' yı seçin. Sonra hataları bir dosyaya yapıştırabilirsiniz. Hataları bir Excel elektronik tablosuna yapıştırırsanız, alanlar farklı sütunlar halinde görünür.

## <a name="ui-element-list"></a>UI Öğe Listesi

Önem derecesi

**Hata listesi** girişi farklı türlerini görüntüler (**hata**, **ileti**, **Uyarı**, **uyarı (etkin)**, **uyarı (etkin olmayan)**.

Kod

Hata kodunu görüntüler.

Description

Girişin metnini görüntüler.

Project

Geçerli projenin adını görüntüler.

Dosya

Dosya adını görüntüler.

Çizgi

Sorunun gerçekleştiği satırı görüntüler.
