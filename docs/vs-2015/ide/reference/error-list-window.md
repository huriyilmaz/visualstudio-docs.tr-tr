---
title: Hata Listesi penceresi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ErrorList
helpviewer_keywords:
- Task List
- build errors
- Error List window
- errors [Visual Studio], Error List window
ms.assetid: b7f6d45a-733b-4ad8-bc2f-737a37509e56
caps.latest.revision: 36
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 35be5ddeedf0b081fa94e399f294151e73a157ed
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657740"
---
# <a name="error-list-window"></a>Hata Listesi Penceresi
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

NOTUN
> Hata Listesi belirli bir hata iletisiyle ilgili bilgileri görüntüler. Hata numarasını veya hata dizesi metnini çıkış penceresinden kopyalayabilirsiniz. Çıkış penceresini göstermek için Ctrl + Alt + O tuşlarına basın. Bkz. [Çıkış penceresi](../../ide/reference/output-window.md).

 **Hata listesi** penceresini kullanarak daha hızlı uygulamalar geliştirebilirsiniz. Örneğin, aşağıdaki görevleri gerçekleştirebilirsiniz:

- Kodu yazarken üretilen hataları, uyarıları ve iletileri görüntüleyin.

- IntelliSense tarafından belirtilen sözdizimi hatalarını bulun.

- Dağıtım hatalarını, belirli statik analiz hatalarını ve Kurumsal Şablon İlkeleri uygulanırken algılanan hataları bulun.

- Sorunun gerçekleştiği dosyayı açmak için herhangi bir hata iletisi girişine çift tıklayın ve hata konumuna gidin.

- Hangi girişlerin görüntülendiğini ve her giriş için hangi bilgi sütunlarının göründüğünü filtreleyin.

- Belirli terimleri arayın ve aramayı yalnızca geçerli proje veya belge ile kapsamını bulun.

  **Hata listesi**görüntülemek Için, **Görünüm/hata listesi**veya **CTRL + \\ + E**' ye tıklayın.

  Farklı bilgi düzeylerini görmek için **hatalar**, **Uyarılar**ve **iletiler** sekmelerini seçebilirsiniz.

  Listeyi sıralamak için herhangi bir sütun başlığına tıklayın. Ek bir sütuna yeniden sıralamak için SHIFT tuşunu basılı tutarak başka bir sütun başlığına tıklayın. Hangi sütunların görüntülendiğini ve gizli olduğunu seçmek için kısayol menüsünde **sütunları göster** ' i seçin. Sütunların görüntülenme sırasını değiştirmek için herhangi bir sütun başlığını sola veya sağa sürükleyin.

> [!NOTE]
> Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza veya sürümüne bağlı olarak burada açıklananlardan farklı bir şekilde farklılık gösterebilir. Ayarlarınızı değiştirmek için **Araçlar/içeri ve dışarı aktarma ayarları**' na tıklayın. Daha fazla bilgi için bkz. [Visual Studio 'Da geliştirme ayarlarını özelleştirme](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="error-list-filters"></a>Hata Listesi filtreleri
 İki açılan kutuda, biri araç çubuğunun sağ tarafında ve diğeri araç çubuğunun solunda olmak üzere iki tür filtre vardır. Araç çubuğunun sol tarafındaki açılan liste, kullanılacak kod dosyası kümesini belirtir (**tüm çözüm**, **Açık belgeler**, **geçerli proje**, **geçerli belge**).

 Arama kapsamını analiz edilecek ve hata gruplarını görecek şekilde kısıtlayabilirsiniz. Örneğin, bir projenin derlenmesini engelleyen temel hatalara odaklanmak isteyebilirsiniz. Kapsam seçenekleri şunlardır:

1. **Açık**belgeler: açık belgeler için hataları, uyarıları ve iletileri göster.

2. **Geçerli proje**: **düzenleyicide** veya seçilen projede seçili olan belgenin projesinden hataları, uyarıları ve iletileri göster **Çözüm Gezgini**.

   > [!NOTE]
   > Şu anda seçili olan belgenin projesi **Çözüm Gezgini**' de seçilen projeden farklıysa, hata, uyarı ve ileti filtrelenmiş listesi değişecektir.

3. **Geçerli belge**: **düzenleyicide** veya **Çözüm Gezgini**seçili olan belge için hataları, uyarıları ve iletileri göster.

   Arama sonuçlarına bir filtre uygulanmışsa, filtrenin adı **hata listesi** başlık çubuğunda görüntülenir. **Hatalar**, **Uyarılar**ve **iletiler** düğmeleri daha sonra toplam öğe sayısıyla birlikte gösterilen filtrelenmiş öğe sayısını görüntüler; Örneğin, düğmeler x/y hata sayısını gösterir. Hiçbir filtre uygulanmazsa, başlık çubuğu yalnızca "Hata Listesi" ifadesini belirtir.

   Araç çubuğunun sağ tarafındaki liste, derlemeden hataların (bir derleme işleminden kaynaklanan hatalar) veya IntelliSense 'den (bir derleme çalıştırılmadan önce algılanan hatalar) veya her ikisiyle ait hataların gösterilip gösterilmeyeceğini belirtir.

## <a name="search"></a>Arayın
 Hata listesindeki belirli hataları bulmak için **hata listesi** araç çubuğunun sağ tarafındaki **arama hata listesi** metin kutusunu kullanın. Hata listesindeki görünür bir sütunda arama yapabilirsiniz ve arama sonuçları her zaman sorgu yerine sıralama önceliği olan sütuna göre sıralanır veya filtre uygulanmış olur. Odak **hata listesi**, **ESC** tuşunu seçerseniz arama terimini ve filtrelenmiş arama sonuçlarını temizleyebilirsiniz. Ayrıca, metin kutusunun sağ tarafındaki **X** simgesini tıklatarak temizleyebilirsiniz.

## <a name="save"></a>Kaydet
 Hata listesini kopyalayabilir ve bir dosyaya kaydedebilirsiniz. Kopyalamak istediğiniz hataları seçin ve seçimi sağ tıklatın, ardından bağlam menüsünde **Kopyala**' yı seçin. Sonra hataları bir dosyaya yapıştırabilirsiniz. Hataları bir Excel elektronik tablosuna yapıştırırsanız, alanlar farklı sütunlar halinde görünür.

## <a name="ui-element-list"></a>UI Öğe Listesi
 Önem derecesi farklı **hata listesi** girişi türlerini (**hata**, **ileti**, **Uyarı**, **uyarı (etkin)**, **uyarı (etkin değil)** görüntüler.

 Kod, hata kodunu görüntüler.

 Açıklama, girişin metnini görüntüler.

 Proje, geçerli projenin adını görüntüler.

 Dosya, dosya adını görüntüler.

 Satır, sorunun gerçekleştiği satırı görüntüler.
