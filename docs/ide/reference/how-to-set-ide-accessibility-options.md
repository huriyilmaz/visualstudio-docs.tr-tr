---
title: 'Nasıl yapılır: IDE erişilebilirlik seçeneklerini ayarlama'
description: Visual Studio 'da kendi tümleşik geliştirme ortamının (IDE), okuma güçlüğü çeken kişiler ve yazma sınırlaması olan kişiler de dahil olmak üzere herkesin kullanması için daha kolay hale gelen erişilebilirlik seçeneklerini nasıl ayarlayacağınızı öğrenin.
ms.date: 08/23/2019
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: how-to
helpviewer_keywords:
- accessibility [Visual Studio]
ms.assetid: ddc96c4c-0600-46c1-8267-7dce4c44ad24
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ac857d961b1ae736645ba2cfda3f1ef5755d0fa1
ms.sourcegitcommit: f27084e64c79e6428746a20dda92795df996fb31
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85770283"
---
# <a name="how-to-set-ide-accessibility-options"></a>Nasıl yapılır: IDE erişilebilirlik seçeneklerini ayarlama

Visual Studio, görme zorluğu olan kişilerin yazmasını ve yazma zorluğu çeken kişileri daha kolay hale getirmeye yönelik özellikler içerir. Örneğin, düzenleyicilerde metnin boyutunu ve rengini değiştirebilir, araç çubuklarında metin ve düğmelerin boyutunu değiştirebilir ve bir işlevi veya ifadeyi tamamlamanıza yardımcı olması için ayarları değiştirebilirsiniz.

Ayrıca, Visual Studio, en sık yazılan karakterleri daha erişilebilir hale getirmek için Dvorak klavye düzenlerini destekler. Ayrıca, Visual Studio ile kullanılabilen varsayılan klavye kısayollarını özelleştirebilirsiniz. Daha fazla bilgi için bkz. [klavye kısayollarını tanımlamak ve özelleştirmek](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

> [!NOTE]
> Gördüğünüz iletişim kutuları ve menü komutları burada açıklananlardan farklı olabilir. Bu, etkin ayarlarınıza veya sürümüne bağlı olarak farklılık gösterebilir. Ayarlarınızı değiştirmek için **Araçlar** menüsünden **Içeri ve dışarı aktarma ayarları** ' nı seçin. Daha fazla bilgi için bkz. [ayarları sıfırlama](../environment-settings.md#reset-settings).

::: moniker range="vs-2017"

> [!TIP]
> Son erişilebilirlik güncelleştirmeleri hakkında daha fazla bilgi edinmek için [Visual Studio 2017 sürüm 15,3](https://devblogs.microsoft.com/visualstudio/accessibility-improvements-in-visual-studio-2017-version-15-3/) blog gönderisine bakın.

::: moniker-end

## <a name="editors-dialogs-and-tool-windows"></a>Düzenleyiciler, diyaloglar ve araç pencereleri

Varsayılan olarak, Visual Studio 'daki iletişim kutuları ve araç pencereleri işletim sistemiyle aynı yazı tipi boyutunu ve renklerini kullanır. IDE, iletişim kutuları, araç çubukları ve araç pencerelerinin çerçevesinin renk ayarları bir renk düzenini temel alarak: açık veya koyu. Seçenekler iletişim kutusunda geçerli renk temasını değiştirebilirsiniz [: ortam > genel](../../ide/reference/general-environment-options-dialog-box.md).

Ayrıca, düzenleyicinin kod görünümünde açılır pencereleri de görüntüleyebilirsiniz. Bu pencereler geçerli nesne üzerindeki kullanılabilir Üyeler ve bir işlevi veya ifadeyi tamamlamaya yönelik parametreler için sizi uyarır. Yazma güçlüğü çekiyorsanız, bu pencereler yararlı olabilir. Ancak, bu kişiler, bazı kullanıcılar için sorunlu olabilecek kod düzenleyicisine odaklanmayı engellemez.

Açılır pencereleri devre dışı bırakma:

1. **Araçlar** menüsünde **Seçenekler**' i seçin.

1. **Metin düzenleyici**  >  **tüm diller**  >  **genel**' i seçin.

1. **Otomatik liste üyeleri** ve **parametre bilgileri** onay kutularını temizleyin.

Tümleşik geliştirme ortamındaki (IDE) pencereleri, çalışma şeklinize en uygun şekilde yeniden düzenleyebilirsiniz. Her bir araç penceresini yerleştirme, kaydırma, gizleme veya otomatik olarak gizleme yapabilirsiniz. Pencere düzenlerini değiştirme hakkında daha fazla bilgi için bkz. [pencere düzenlerini özelleştirme](../../ide/customizing-window-layouts-in-visual-studio.md).

### <a name="change-the-size-of-text"></a>Metin boyutunu değiştirme

**Araç** **Command** **Immediate** **Output**  >  **seçenekleri**  >  **ortam**  >  **yazı tiplerini ve renklerini**kullanarak komut penceresi, anlık pencere ve çıkış penceresi gibi metin tabanlı araç pencerelerinin ayarlarını değiştirebilirsiniz.

**Ayarları göster** açılan listesinde **[tüm metin araç pencereleri]** seçeneğini belirlediğinizde, varsayılan ayar **öğe ön planı** ve **öğe arka plan** açılan listelerinde **varsayılan** olarak listelenir. Bu ayarları değiştirmek için **özel** düğmesini seçin.

Ayrıca, metnin düzenleyicide nasıl görüntüleneceği için ayarları değiştirebilirsiniz. Aşağıdaki adımları uygulayın:

1. **Araçlar** menüsünde **Seçenekler**' i seçin.

1. **Ortam**  >  **yazı tiplerini ve renklerini**seçin.

1. **Ayarları göster** açılan menüsünde bir seçenek belirleyin.

    Bir düzenleyicideki metnin yazı tipi boyutunu değiştirmek için **metin düzenleyici**' yi seçin.

    Metin tabanlı araç penceresinde metnin yazı tipi boyutunu değiştirmek için **[tüm metin araç pencereleri]** öğesini seçin.

    Bir düzenleyicideki Araç Ipucu metninin yazı tipi boyutunu değiştirmek için **Düzenleyici araç ipucu**' nu seçin.

    Ekstre tamamlama açılır penceresinde metin yazı tipi boyutunu değiştirmek için, **ekstre tamamlama**' yı seçin.

1. **Görüntüleme öğelerinden** **düz metin**' i seçin.

1. **Yazı tipi**' nde yeni bir yazı tipi türü seçin.

1. **Boyut**' da, yeni bir yazı tipi boyutu seçin.

    > [!TIP]
    > Metin tabanlı araç pencereleri ve düzenleyicilerinin metin boyutunu sıfırlamak için **Varsayılanları Kullan**' ı seçin.

7. **Tamam ' ı**seçin.

### <a name="change-the-colors-that-are-used-in-the-ide"></a>IDE 'de kullanılan renkleri değiştirme

Metin, kenar boşluğu göstergeleri, boşluk ve düzenleyicideki kod öğeleri için varsayılan renkleri değiştirmeyi tercih edebilirsiniz. Aşağıdaki adımları uygulayın:

1. **Araçlar** menüsünde **Seçenekler**' i seçin.

1. **Ortam** klasöründe, **yazı tipleri ve renkler**' i seçin.

1. **Ayarları göster**bölümünde **metin düzenleyici**' yi seçin.

1. **Görüntüleme öğelerinden** **düz metin**, **Gösterge kenar boşluğu**, **görünür**boşluk, **HTML öznitelik adı**veya **XML özniteliği**gibi görüntülemesi gereken görünümü olan bir öğe seçin.

1. Aşağıdaki seçeneklerden görüntüleme ayarları ' nı seçin: **öğe ön planı**, **öğe arka planı**ve **kalın**.

1. **Tamam ' ı**seçin.

> [!TIP]
> İşletim sisteminizdeki tüm uygulama pencerelerinin yüksek karşıtlık renklerini kullanmak için **sol alt** + **Sol SHIFT** + **PrtScn**tuşuna basın. Visual Studio açıksa, yüksek karşıtlık renklerini tam olarak uygulamak için kapatın ve yeniden açın.

## <a name="toolbars"></a>Araç Çubukları

Araç çubuğu kullanılabilirliğini ve erişilebilirliğini geliştirmek için araç çubuğu düğmelerine metin ekleyebilirsiniz.

### <a name="to-assign-text-to-toolbar-buttons"></a>Araç çubuğu düğmelerine metin atamak için

1. **Araçlar** menüsünde **Özelleştir**' i seçin.

1. **Özelleştir** Iletişim kutusunda **Komutlar** sekmesini seçin.

1. **Araç çubuğu**' nu seçin ve ardından metnini görüntülemeyi düşündüğünüz düğmeyi içeren araç çubuğu adını seçin.

1. Listede, değiştirmek istediğiniz komutu seçin.

1. **Seçimi Değiştir**' i seçin.

1. **Görüntü ve metin**seçin.

### <a name="to-modify-the-displayed-text-in-a-button"></a>Bir düğmedeki görüntülenecek metni değiştirmek için

1. **Seçimi Değiştir**' i yeniden seçin.

1. **Ad**alanına bitişik, Ekle seçili düğme için yeni bir başlık girin.

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio 'nun erişilebilirlik özellikleri](../../ide/reference/accessibility-features-of-visual-studio.md)
* [Mac için Visual Studio için erişilebilirlik](/visualstudio/mac/accessibility/)
* [Erişilebilir uygulamalar tasarlamak için kaynaklar](../../ide/reference/resources-for-designing-accessible-applications.md)
