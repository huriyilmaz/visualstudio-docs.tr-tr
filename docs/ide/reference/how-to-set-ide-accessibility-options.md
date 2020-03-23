---
title: 'Nasıl yapılı: IDE erişilebilirlik seçeneklerini ayarlama'
description: Visual Studio'da, okuma sı düşük görme yetisine sahip kişiler ve yazma becerisi sınırlı kişiler de dahil olmak üzere, entegre geliştirme ortamını (IDE) herkesin kullanmasını kolaylaştıracak erişilebilirlik seçeneklerini nasıl belirleyeceğinizi öğrenin.
ms.date: 08/23/2019
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- accessibility [Visual Studio]
ms.assetid: ddc96c4c-0600-46c1-8267-7dce4c44ad24
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 63bba4e8defcd727f05dbc209aa2f48f7d5f2c92
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "70107777"
---
# <a name="how-to-set-ide-accessibility-options"></a>Nasıl yapılı: IDE erişilebilirlik seçeneklerini ayarlama

Visual Studio, görme yetisi düşük olan kişilerin okumasını ve yazma becerisi sınırlı olan kişiler için daha kolay olmasını sağlayan özellikler içerir. Örneğin, düzenleyicilerdeki metnin boyutunu ve rengini değiştirebilir, araç çubuklarındaki metin ve düğmelerin boyutunu değiştirebilir ve bir işlevi veya deyimi tamamlamanıza yardımcı olacak ayarları değiştirebilirsiniz.

Buna ek olarak, Visual Studio en sık yazılan karakterleri daha erişilebilir hale getiren Dvorak klavye düzenlerini destekler. Visual Studio ile kullanılabilen varsayılan klavye kısayollarını da özelleştirebilirsiniz. Daha fazla bilgi için [bkz.](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)

> [!NOTE]
> Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza veya sürüme bağlı olarak değişebilen burada açıklananlardan farklı olabilir. Ayarlarınızı değiştirmek için **Araçlar** menüsünde **Ayarlar İçe Ve Dışa Aktar'ı** seçin. Daha fazla bilgi [için, ayarları Sıfırla'ya](../environment-settings.md#reset-settings)bakın.

::: moniker range="vs-2017"

> [!TIP]
> En son erişilebilirlik güncelleştirmeleri hakkında daha fazla bilgi edinmek için [Visual Studio 2017 sürüm 15.3 blog gönderisinde Erişilebilirlik geliştirmelerine](https://devblogs.microsoft.com/visualstudio/accessibility-improvements-in-visual-studio-2017-version-15-3/) bakın.

::: moniker-end

## <a name="editors-dialogs-and-tool-windows"></a>Editörler, iletişim kutuları ve araç pencereleri

Varsayılan olarak, Visual Studio'daki iletişim kutuları ve araç pencereleri işletim sistemiyle aynı yazı tipi boyutunu ve renklerini kullanır. IDE, iletişim kutuları, araç çubukları ve araç pencerelerinin çerçevesiiçin renk ayarları bir renk düzenine dayanır: açık veya koyu. Seçenekler iletişim kutusundaki geçerli renk temesini [değiştirebilirsiniz: Ortam > Genel.](../../ide/reference/general-environment-options-dialog-box.md)

Ayrıca, düzenleyicinin Kod görünümünde açılır pencereleri de görüntüleyebilirsiniz. Bu pencereler, bir işlevi veya deyimi tamamlamak için geçerli nesne ve parametreler üzerinde kullanılabilir üyeler ile isteyebilir. Bu pencereler yazmakta güçlük çekiyorsanız yararlı olabilir. Ancak, bazı kullanıcılar için sorunlu olabilir kod düzenleyicisi, odak müdahale.

Açılır pencereleri şu şekilde kapatabilirsiniz:

1. **Araçlar** menüsünden **Seçenekler'i**seçin.

1. **Metin Düzenleyici** > **Tüm Diller** > **Genel**seçin.

1. Otomatik **liste üyelerini** ve **Parametre bilgi** onay kutularını temizleyin.

Tümleşik geliştirme ortamındaki (IDE) pencereleri çalışma şeklinize en uygun şekilde yeniden düzenleyebilirsiniz. Her araç pencereni sabitleyebilir, yüzdürebilir, gizleyebilir veya otomatik olarak gizleyebilirsiniz. Pencere düzenlerini nasıl değiştireceğimiz hakkında daha fazla bilgi için [bkz.](../../ide/customizing-window-layouts-in-visual-studio.md)

### <a name="change-the-size-of-text"></a>Metin boyutunu değiştirme

**Komut** penceresi, **Hemen** penceresi ve **Çıktı** penceresi gibi metin tabanlı araç pencerelerinin ayarlarını **Araçlar** > **Seçenekleri** > **Ortamı** > **Yazı Tipleri ve Renkleri'ni**kullanarak değiştirebilirsiniz.

Açılan liste **için Göster ayarlarında** **[Tüm Metin Aracı Windows]** seçeneğini seçtiğinizde, varsayılan ayar **Öğe ön planında** ve Öğe **arka planı** açılır listelerinde **Varsayılan** olarak listelenir. Bu ayarları değiştirmek için **Özel** düğmesini seçin.

Ayrıca, metnin düzenleyicide nasıl görüntüleneceğine yönelik ayarları da değiştirebilirsiniz. Aşağıdaki adımları uygulayın:

1. **Araçlar** menüsünden **Seçenekler'i**seçin.

1. **Çevre** > **Yazı Tipleri ve Renkleri**seçin.

1. Açılan menü **için Göster ayarlarında** bir seçenek seçin.

    Bir düzenleyicideki metin için yazı tipi boyutunu değiştirmek için **Metin Düzenleyicisi'ni**seçin.

    Metin tabanlı araç pencerelerinde metin yazı tipi boyutunu değiştirmek için **[Tüm Metin Aracı Windows]** seçeneğini belirleyin.

    Bir düzenleyicideki ToolTip metninin yazı tipi boyutunu değiştirmek için **Düzenleyici Araç İpucu'nu**seçin.

    Deyim tamamlama açılır pencerelerinde metin için yazı tipi boyutunu değiştirmek için **Deyim Tamamlama'yı**seçin.

1. **Görüntü öğelerinden** **Düz Metin'i**seçin.

1. **Yazı Tipi'nde**yeni bir yazı tipi seçin.

1. **Boyut,** yeni bir yazı tipi boyutu seçin.

    > [!TIP]
    > Metin tabanlı araç pencereleri ve düzenleyiciler için metin boyutunu sıfırlamak için **Varsayılanları Kullan'ı**seçin.

7. **Tamam'ı**seçin.

### <a name="change-the-colors-that-are-used-in-the-ide"></a>IDE'de kullanılan renkleri değiştirme

Düzenleyicideki metin, kenar boşluğu göstergeleri, beyaz alan ve kod öğeleri için varsayılan renkleri değiştirmeyi seçebilirsiniz. Aşağıdaki adımları uygulayın:

1. **Araçlar** menüsünden **Seçenekler'i**seçin.

1. **Çevre** klasöründe **Yazı Tipleri ve Renkler'i**seçin.

1. **Için Göster ayarlarında,** **Metin Düzenleyici'yi**seçin.

1. **Görüntü öğelerinden,** **Düz Metin,** **Gösterge Kenar Boşluğu,** Görünür Beyaz **Boşluk,** HTML Öznitelik Adı veya **XML** **Özniteliği**gibi ekranı değiştirmeniz gereken bir öğe seçin.

1. Aşağıdaki seçeneklerden ekran ayarlarını seçin: **Öğe ön planı,** **Öğe arka planı**ve **Kalın**.

1. **Tamam'ı**seçin.

> [!TIP]
> İşletim sisteminizdeki tüm uygulama pencereleri için yüksek kontrastlı renkler kullanmak için **Sol Alt**+**Sol Shift**+**PrtScn**tuşuna basın. Visual Studio açıksa, yüksek kontrastlı renkleri tam olarak uygulamak için kapatın ve yeniden açın.

## <a name="toolbars"></a>Araç Çubukları

Araç çubuğu kullanılabilirliğini ve erişilebilirliği artırmak için araç çubuğu düğmelerine metin ekleyebilirsiniz.

### <a name="to-assign-text-to-toolbar-buttons"></a>Araç çubuğu düğmelerine metin atamak için

1. **Araçlar** menüsünden **Özelleştir'i**seçin.

1. **Özelleştir** iletişim kutusunda **Komutlar** sekmesini seçin.

1. **Araç Çubuğu'nu**seçin ve ardından metni görüntülemek istediğiniz düğmeyi içeren araç çubuğu adını seçin.

1. Listede, değiştirmek istediğiniz komutu seçin.

1. **Seçimi Değiştir'i**seçin.

1. **Resim ve Metin'i**seçin.

### <a name="to-modify-the-displayed-text-in-a-button"></a>Düğmede görüntülenen metni değiştirmek için

1. **Seçimi Değiştir'i**yeniden seçin.

1. **In Name'e**bitişik olarak, seçili düğme için yeni bir alt yazı ekleyin.

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio'nun erişilebilirlik özellikleri](../../ide/reference/accessibility-features-of-visual-studio.md)
* [Mac için Visual Studio için erişilebilirlik](/visualstudio/mac/accessibility/)
* [Erişilebilir uygulamalar tasarlamak için kaynaklar](../../ide/reference/resources-for-designing-accessible-applications.md)
