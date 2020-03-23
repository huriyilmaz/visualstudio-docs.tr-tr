---
title: IDE'de nasıl hareket edilebilen
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- environments [Visual Studio], navigation
- documents [Visual Studio], navigating
- IDE, navigation
- navigation [Visual Studio]
- files [Visual Studio], navigating between
- windows [Visual Studio], navigating
- Window.NextDocumentWindowNav
- IDE navigator
ms.assetid: 6c36b6eb-c93f-496b-af08-4199f7afd8bd
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2febdedf5cf472132de936c37cad787df3d77518
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591001"
---
# <a name="how-to-move-around-in-the-visual-studio-ide"></a>Nasıl yapılır: Visual Studio IDE'de hareket edin

Tümleşik geliştirme ortamı (IDE), tercihinize veya proje gereksinimlerinize bağlı olarak pencereden pencereye ve dosyadan dosyaya birkaç farklı şekilde dosyaya geçmenize olanak sağlayacak şekilde tasarlanmıştır. Düzenleyicideki açık dosyalar arasında geçiş yapmayı veya IDE'deki tüm etkin araç pencerelerinde geçiş yapmayı seçebilirsiniz. Ayrıca, en son erişildiği sıraya bakılmaksızın, doğrudan düzenleyicide açık olan herhangi bir dosyaya geçebilirsiniz. Bu özellikler, IDE'de çalışırken üretkenliğinizi artırmaya yardımcı olabilir.

> [!NOTE]
> İletişim kutularında bulunan seçenekler ve gördüğünüz menü komutlarının adları ve konumları, etkin ayarlarınıza veya sürüme bağlı olarak bu makalede açıklanandan farklı olabilir. Bu makale **genel** ayarlar göz önünde bulundurularak yazılmıştır. Ayarlarınızı değiştirmek için, örneğin **Genel** veya **Görsel C++** ayarlarını değiştirmek **için, Araçlar** > **İçe Ve Dışa Aktar Ayarlarını**seçin ve ardından **tüm ayarları sıfırla'yı**seçin.

## <a name="keyboard-shortcuts"></a>Klavye kısayolları

Visual Studio'daki hemen hemen her menü komutunda klavye kısayolu vardır. Ayrıca kendi özel kısayolları oluşturabilirsiniz. Daha fazla bilgi için [bkz.](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)

## <a name="navigate-among-files-in-the-editor"></a>Düzenleyicideki dosyalar arasında gezinme

Düzenleyicide açık olan dosyalar arasında gezinmek için çeşitli yöntemler kullanabilirsiniz. Dosyalar arasında, bunlara erişme sıranıza göre hareket edebilir, şu anda açık olan dosyaları hızlı bir şekilde bulmak için IDE Gezgini'ni kullanabilir veya sık kullanılan dosyaları her zaman görünür olmaları için sekmeye sabitleyebilirsiniz.

Microsoft Internet Explorer'daki görüntüleme geçmişiniz için ileri ve geri gibi, erişilme sırasına göre düzenleyicideki açık dosyalar arasında geriye doğru gidin ve ileri döneçlerde gidin.

### <a name="to-move-through-open-files-in-order-of-use"></a>Açık dosyalar arasında kullanım sırasına göre geçiş yapmak için

- Açık belgeleri en son dokundukları sırada etkinleştirmek için **Ctrl** + **-** (tire) tuşuna basın.

- Açık belgeleri ters sırada etkinleştirmek için **Ctrl**+**Shift** + **-** (tire) tuşuna basın.

    > [!NOTE]
    > **İleri Git** ve **İleri** Git de **Görünüm** menüsünde bulunabilir.

Ayrıca, dosyaya en son ne zaman eriştüğüne bakılmaksızın, **ide Navigator,** düzenleyicideki **Etkin Dosyalar** listesini veya **Windows** iletişim kutusunu kullanarak düzenleyicide açık olan belirli bir dosyaya da geçebilirsiniz.

**IDE Navigator** çok Windows uygulama değiştirici gibi çalışır. Menülerden kullanılamaz ve yalnızca kısayol tuşları kullanılarak erişilebilir. Geçiş yapmak istediğiniz sıraya bağlı olarak, dosyalar arasında geçiş yapmak için **IDE Navigator'a** (aşağıda gösterildiği şekilde) erişmek için iki komuttan birini kullanabilirsiniz.

![Görsel Stüdyo IDE Navigasyon](../ide/media/vs2015_ide_navigator.png)

`Window.PreviousDocumentWindowNav`en son erişilen dosyaya geçmenizi `Window.NextDocumentWindowNav` ve ters sırada hareket etmenizi sağlar. **Genel Geliştirme Ayarları** **Shift**+**Alt**+ `Window.PreviousDocumentWindowNav` F7'yi `Window.NextDocumentWindowNav`ve **Alt**+**F7** **F7'yi** .

> [!NOTE]
> Kullanmakta olduğunuz ayarlar birleşimi bu komuta atanmış bir kısayol tuşu birleşimi yoksa, **Seçenekler** iletişim kutusunun **Klavye** sayfasını kullanarak kendi özel komutunuzu atayabilirsiniz. Daha fazla bilgi için [bkz.](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)

### <a name="to-switch-to-specific-files-in-the-editor"></a>Düzenleyicideki belirli dosyalara geçmek için

- **IDE Navigator'ı**görüntülemek için **Ctrl**+**Sekmesine** basın. **Ctrl** tuşuna basılı tutun ve geçmek istediğiniz dosyayı seçene kadar **Sekme'ye** tekrar tekrar basın.

    > [!TIP]
    > **Etkin Dosyalar** listesinden geçme sırasını tersine çevirmek için **Ctrl**+**Shift** tuşlarını basılı tutun ve **Sekme tuşuna**basın.

    \-veya -

- Düzenleyicinin sağ üst **köşesinde, Etkin Dosyalar** düğmesini seçin ve ardından listeden geçmek için bir dosya seçin.

    \-veya -

- Menü çubuğunda **Pencere** > **Pencerelerini**seçin.

- Listede görüntülemek istediğiniz dosyayı seçin ve ardından **Etkinleştir'i**seçin.

## <a name="navigate-among-tool-windows-in-the-ide"></a>IDE'deki araç pencereleri arasında gezinme

**IDE Navigator** ayrıca IDE'de açık olan araç pencerelerinden geçmenizi sağlar. Geçiş yapmak istediğiniz sıraya bağlı olarak, araç pencerelerinde geçiş yapmak için **IDE** Gezgini'ne erişmek için iki komuttan birini kullanabilirsiniz. `Window.PreviousToolWindowNav`en son erişilen dosyaya geçmenizi `Window.NextToolWindowNav` ve ters sırada hareket etmenizi sağlar. **Genel Geliştirme Ayarları** **Shift**+**Alt**+ `Window.PreviousDocumentWindowNav` F7'yi `Window.NextDocumentWindowNav`ve **Alt**+**F7** **F7'yi** .

> [!NOTE]
> Kullanmakta olduğunuz ayarlar birleşimi bu komuta atanmış bir kısayol tuşu birleşimi yoksa, **Seçenekler** iletişim kutusunun **Klavye** sayfasını kullanarak kendi özel komutunuzu atayabilirsiniz. Daha fazla bilgi için [bkz.](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)

### <a name="to-switch-to-a-specific-tool-window-in-the-ide"></a>IDE'de belirli bir araç penceresine geçmek için

- **IDE Navigator'ı**görüntülemek için **Alt**+**F7** tuşuna basın. **Alt** tuşunu basılı tutun ve geçmek istediğiniz pencereyi seçene kadar **F7** tuşuna tekrar tekrar basın.

    > [!TIP]
    > **Etkin Araç Windows** listesinden geçme sıranızı tersine çevirmek için **Shift**+**Alt** tuşlarını basılı tutun ve **F7 tuşuna**basın.

## <a name="see-also"></a>Ayrıca bkz.

- [Pencere düzenlerini özelleştirme](../ide/customizing-window-layouts-in-visual-studio.md)
- [Varsayılan klavye kısayolları](../ide/default-keyboard-shortcuts-in-visual-studio.md)
