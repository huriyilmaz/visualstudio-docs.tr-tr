---
title: 'Nasıl yapabilirsiniz: IDE erişilebilirlik seçeneklerini ayarlama'
description: Görme zoru olan kişiler ve yazma azlığı olan kişiler de dahil olmak üzere tümleşik geliştirme ortamını (IDE) herkesin kullanımına kolaylaştıracak şekilde Visual Studio'de erişilebilirlik seçeneklerini ayarlamayı öğrenin.
ms.date: 08/23/2019
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: how-to
helpviewer_keywords:
- accessibility [Visual Studio]
ms.assetid: ddc96c4c-0600-46c1-8267-7dce4c44ad24
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4963066cfd2347bff219845c74522915652ef28f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122151528"
---
# <a name="how-to-set-ide-accessibility-options"></a>Nasıl yapabilirsiniz: IDE erişilebilirlik seçeneklerini ayarlama

Visual Studio, görme zorlu kişilerin okuması ve sınırlı kişilikleri olan kişilerin yazmalarını kolaylaştıran özellikler içerir. Örneğin düzenleyicilerde metnin boyutunu ve rengini değiştirebilir, araç çubuğundaki metin ve düğmelerin boyutunu değiştirebilir ve bir işlevi veya deyimi tamamlamanıza yardımcı olacak ayarları değiştirebilirsiniz.

Ayrıca, Visual Studio karakterlerini daha erişilebilir hale alan Dvorak klavye düzenlerini destekler. Ayrıca, bu kısayollarla kullanılabilen varsayılan klavye kısayollarını Visual Studio. Daha fazla bilgi için [bkz. Klavye kısayollarını tanımlama ve özelleştirme.](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)

> [!NOTE]
> Gördüğünüz iletişim kutuları ve menü komutları burada açıklananlardan farklı olabilir ve bu, etkin ayarlarınıza veya sürümünüze bağlı olarak değişebilir. Ayarlarınızı değiştirmek için Araçlar menüsünde İçeri ve Dışarı  **Ayarlar'yi** seçin. Daha fazla bilgi için [bkz. Ayarları sıfırlama.](../environment-settings.md#reset-settings)

::: moniker range="vs-2017"

> [!TIP]
> Son erişilebilirlik güncelleştirmeleri hakkında daha fazla bilgi edinmek için [Visual Studio 2017 sürüm 15.3](https://devblogs.microsoft.com/visualstudio/accessibility-improvements-in-visual-studio-2017-version-15-3/) blog gönderisi'ne bakın.

::: moniker-end

## <a name="editors-dialogs-and-tool-windows"></a>Düzenleyiciler, iletişim kutuları ve araç pencereleri

Varsayılan olarak, iletişim kutuları ve araç pencereleri Visual Studio sistemiyle aynı yazı tipi boyutunu ve renklerini kullanır. IDE çerçevesi, iletişim kutuları, araç çubukları ve araç pencerelerinin renk ayarları, açık veya koyu renk düzenini temel almaktadır. Seçenekler iletişim kutusunda geçerli renk temasını [değiştirebilirsiniz: Ortam >.](../../ide/reference/general-environment-options-dialog-box.md)

Açılır pencereleri düzenleyicinin Kod görünümünde de görüntüebilirsiniz. Bu pencereler, geçerli nesnede kullanılabilir üyeleri ve bir işlevi veya deyimi tamamlamak için parametreleri girmenizi ister. Bu pencereler, yazmada zorluk yaşadıysanız yararlı olabilir. Ancak, bazı kullanıcılar için sorunlu olabilir kod düzenleyicisinde odakla müdahale ediyor olabilir.

Açılır pencereleri şu şekilde kapat:

1. Araçlar menüsünde **Seçenekler'i** **seçin.**

1. Metin **Düzenleyici Tüm** Diller  >  **Genel'i**  >  **seçin.**

1. Üyeleri otomatik **olarak listele ve** **Parametre bilgileri onay** kutularını temizleyin.

Tümleşik geliştirme ortamındaki (IDE) pencereleri çalışma yollarına en uygun şekilde yeniden düzenleyebilirsiniz. Her araç penceresini dock, float, hide veya otomatik olarak gizleyebilirsiniz. Pencere düzenlerini değiştirme hakkında daha fazla bilgi için [bkz. Pencere düzenlerini özelleştirme.](../../ide/customizing-window-layouts-in-visual-studio.md)

### <a name="change-the-size-of-text"></a>Metin boyutunu değiştirme

Araç Seçenekleri Ortam Yazı Tipleri ve Renkler'i kullanarak  Komut **penceresi,** Anlık pencere ve **Çıkış** penceresi gibi metin tabanlı araç pencerelerinin  >    >    >  **ayarlarını değiştirebilirsiniz.**

Açılan liste için ayarları **göster listesinde [Tüm Metin Aracı Windows]** öğesini seçerek varsayılan ayar  Öğe ön  planı ve Öğe arka plan açılır listelerinde Varsayılan olarak listelenir.   Bu ayarları **değiştirmek** için Özel düğmesini seçin.

Düzenleyicide metnin görüntülenme şekliyle ilgili ayarları da değiştirebilirsiniz. Aşağıdaki adımları uygulayın:

1. Araçlar menüsünde **Seçenekler'i** **seçin.**

1. Ortam Yazı **Tipleri**  >  **ve Renkler'i seçin.**

1. Ayarları göster açılan **menüsünden bir** seçenek belirleyin.

    Düzenleyicide metnin yazı tipi boyutunu değiştirmek için Metin **Düzenleyici'yi seçin.**

    Metin tabanlı araç pencerelerde metnin yazı tipi boyutunu değiştirmek için [Tüm Metin Aracı **Windows] 'i seçin.**

    Düzenleyicide ToolTip metninin yazı tipi boyutunu değiştirmek için Düzenleyici Araç **İpucu'nı seçin.**

    Deyim tamamlama açılır pencerelerde metnin yazı tipi boyutunu değiştirmek için Deyim **Tamamlama'ya basın.**

1. Öğeleri **görüntüle'den** Düz **Metin'i seçin.**

1. Yazı **Tipi'nin** altında yeni bir yazı tipi türü seçin.

1. **Boyut'ta** yeni bir yazı tipi boyutu seçin.

    > [!TIP]
    > Metin tabanlı araç pencerelerine ve düzenleyicilere metin boyutunu sıfırlamak için Varsayılanları **Kullan'ı seçin.**

7. **Tamam'ı seçin.**

### <a name="change-the-colors-that-are-used-in-the-ide"></a>IDE'de kullanılan renkleri değiştirme

Düzenleyicide metin, kenar boşluğu göstergeleri, boşluk ve kod öğeleri için varsayılan renkleri değiştirebilirsiniz. Aşağıdaki adımları uygulayın:

1. Araçlar menüsünde **Seçenekler'i** **seçin.**

1. Ortam klasöründe **Yazı** Tipleri ve **Renkler'i seçin.**

1. Için **ayarları göster'de Metin** **Düzenleyici'yi seçin.**

1. Öğeleri **görüntüle'den** Düz Metin, Gösterge Kenar Boşluğu, Görünür **Boşluk,** **HTML** Öznitelik Adı veya XML Özniteliği gibi görüntülemesi gereken **bir öğeyi seçin.**  

1. Şu seçeneklerden görüntü ayarlarını seçin: **Öğe ön planı, Öğe** arka **planı** ve **Kalın**.

1. **Tamam'ı seçin.**

> [!TIP]
> İşletim sisteminiz üzerinde tüm uygulama pencerelerine yüksek karşıtlık renkleri kullanmak için Sol **Alt Sol** + **Shift** + **PrtScn tuşlarına basın.** Açık Visual Studio, yüksek karşıtlıklı renkleri tam olarak uygulamak için kapatın ve yeniden açın.

## <a name="toolbars"></a>Araç Çubukları

Araç çubuğunun kullanılabilirliğini ve erişilebilirliğini geliştirmek için araç çubuğu düğmelerine metin ekleyebilirsiniz.

### <a name="to-assign-text-to-toolbar-buttons"></a>Araç çubuğu düğmelerine metin atamak için

1. Araçlar menüsünde **Özelleştir'i** **seçin.**

1. Özelleştir **iletişim** kutusunda Komutlar **sekmesini** seçin.

1. Araç **Çubuğu'nu** seçin ve ardından metin görüntülemek istediğiniz düğmeyi içeren araç çubuğu adını seçin.

1. Listede, değiştirmek istediğiniz komutu seçin.

1. Seçimi **Değiştir'i seçin.**

1. Görüntü ve **Metin'i seçin.**

### <a name="to-modify-the-displayed-text-in-a-button"></a>Bir düğmede görüntülenen metni değiştirmek için

1. Seçimi **Değiştir'i yeniden seçin.**

1. Ad'ın **yanında,** ekle seçeneği seçili düğme için yeni bir açıklamalı alt yazı girin.

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio'nin erişilebilirlik özellikleri](../../ide/reference/accessibility-features-of-visual-studio.md)
* [Mac için Visual Studio için erişilebilirlik](/visualstudio/mac/accessibility/)
* [Erişilebilir uygulamalar tasarlama kaynakları](../../ide/reference/resources-for-designing-accessible-applications.md)
