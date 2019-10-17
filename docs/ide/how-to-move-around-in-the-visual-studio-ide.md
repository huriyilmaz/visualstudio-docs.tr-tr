---
title: IDE 'de gezinme
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8764ccc5a662a40559b6b7ab4f19cdff0e2d555e
ms.sourcegitcommit: e82baa50bf5a65858c410882c2e86a552c2c1921
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72381325"
---
# <a name="how-to-move-around-in-the-visual-studio-ide"></a>Nasıl yapılır: Visual Studio IDE 'de gezinme

Tümleşik geliştirme ortamı (IDE), tercihlerinize veya proje gereksinimlerinize bağlı olarak, pencereden pencereye ve dosyaya farklı yollarla dosya taşımanıza olanak tanımak üzere tasarlanmıştır. Düzenleyicideki açık dosyalar arasında dolaşmayı veya IDE 'deki tüm etkin araç pencerelerini kullanarak geçiş yapabilirsiniz. Ayrıca, son erişildiği sırada ne olursa olsun, düzenleyicide açık olan herhangi bir dosyaya doğrudan geçiş yapabilirsiniz. Bu özellikler, IDE 'de çalışırken üretkenliğinizi artırmaya yardımcı olabilir.

> [!NOTE]
> İletişim kutularında kullanılabilen seçenekler ve gördüğünüz menü komutlarının adları ve konumları, etkin ayarlarınıza veya sürümüne bağlı olarak bu makalede açıklananlar arasından farklılık gösterebilir. Bu makale, **genel** ayarlar göz önünde bulundurularak yazılmıştır. Ayarlarınızı değiştirmek için (örneğin, **genel** veya  **C++ görsel** ayarları), **Araçlar** > **içeri ve dışarı aktarma ayarları**' nı seçin ve ardından **tüm ayarları Sıfırla**' yı seçin.

## <a name="keyboard-shortcuts"></a>Klavye kısayolları

Visual Studio 'daki neredeyse her menü komutunun bir klavye kısayolu vardır. Kendi özel kısayollarınızı da oluşturabilirsiniz. Daha fazla bilgi için bkz. [klavye kısayollarını tanımlamak ve özelleştirmek](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

## <a name="navigate-among-files-in-the-editor"></a>Düzenleyicideki dosyalar arasında gezinme

Düzenleyicide açık olan dosyalar arasında gezinmek için çeşitli yöntemler kullanabilirsiniz. Dosyalara erişmek istediğiniz sıraya göre dosyalar arasında geçiş yapabilirsiniz, daha önce açık olan herhangi bir dosyayı hızlı bir şekilde bulmak için IDE gezginini kullanın veya her zaman görünür olmaları için sık kullanılan dosyaları sekmeye uygun olarak sabitleyin.

Geriye doğru ilerleyin ve Microsoft Internet Explorer 'da görüntüleme geçmişiniz için, geri ve ileri ' ye benzer şekilde, düzenleyicide bulunan açık dosyalar üzerinden ileri döngülerine gidin.

### <a name="to-move-through-open-files-in-order-of-use"></a>Açık dosyalar aracılığıyla kullanım sırasıyla geçiş yapmak için

- Açık belgeleri en son dokundukları sırada etkinleştirmek için **Ctrl**+ **-** (kısa çizgi) tuşlarına basın.

- Açık belgeleri ters sırada etkinleştirmek için **Ctrl**+**SHIFT**+ **-** (kısa çizgi) tuşlarına basın.

    > [!NOTE]
    > **Geriye giderek** **İleri** git **Görünüm** menüsünde de bulunabilir.

Ayrıca, dosyaya son erişiminizden bağımsız olarak, **IDE Gezginini**, düzenleyicide **etkin dosyalar** listesini veya **Windows** iletişim kutusunu kullanarak, düzenleyicide açık olan belirli bir dosyaya geçiş yapabilirsiniz.

**IDE Gezgini** , Windows uygulama değiştiricisinden çok benzer şekilde çalışmaktadır. Menülerden kullanılamaz ve yalnızca kısayol tuşları kullanılarak erişilebilir. **IDE Gezginine** erişmek için iki komuttan birini kullanabilirsiniz (aşağıda gösterildiği gibi), üzerinde geçiş yapmak istediğiniz sıraya bağlı olarak dosyalar arasında geçiş yapmak için iki komuttan yararlanabilirsiniz.

![Visual Studio IDE Gezgini](../ide/media/vs2015_ide_navigator.png)

`Window.PreviousDocumentWindowNav`, en son erişilen dosyaya taşımanızı sağlar ve `Window.NextDocumentWindowNav` ' i ters sırada taşımanızı sağlar. **Genel geliştirme ayarları** **SHIFT**+**alt**+**F7** `Window.PreviousDocumentWindowNav` ve **alt**+**F7** 0 ' a atar.

> [!NOTE]
> Kullandığınız ayarlar birleşimine bu komuta atanmış kısayol tuşu birleşimi zaten yoksa, **Seçenekler** Iletişim kutusunun **klavye** sayfasını kullanarak kendi özel komutunuzu atayabilirsiniz. Daha fazla bilgi için bkz. [klavye kısayollarını tanımlamak ve özelleştirmek](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

### <a name="to-switch-to-specific-files-in-the-editor"></a>Düzenleyicideki belirli dosyalara geçiş yapmak için

- **IDE Gezginini**göstermek için **CTRL**+**Tab** tuşlarına basın. **CTRL** tuşunu basılı tutun ve geçiş yapmak istediğiniz dosyayı seçene kadar **sekme** tuşuna basın.

    > [!TIP]
    > **Etkin dosyalar** listesinden gittiğiniz sırayı tersine çevirmek için **CTRL**+**Shift** tuşlarını basılı tutup **Tab**tuşuna basın.

    \- veya-

- Düzenleyicinin sağ üst köşesinde **etkin dosyalar** düğmesini seçin ve ardından listeden bir dosyayı seçerek geçiş yapın.

    \- veya-

- Menü çubuğunda **, @no__t-** 1**Windows**' u seçin.

- Listede, görüntülemek istediğiniz dosyayı seçin ve ardından **Etkinleştir**' i seçin.

## <a name="navigate-among-tool-windows-in-the-ide"></a>IDE 'deki araç pencereleri arasında gezinme

**IDE Gezgini** , IDE 'de açtığınız araç pencereleri arasında geçiş yapmanızı de sağlar. **IDE Gezginine** erişmek için iki komuttan birini kullanarak, geçiş yapmak istediğiniz sıraya bağlı olarak araç pencereleri arasında geçiş yapabilirsiniz. `Window.PreviousToolWindowNav`, en son erişilen dosyaya taşımanızı sağlar ve `Window.NextToolWindowNav` ' i ters sırada taşımanızı sağlar. **Genel geliştirme ayarları** **SHIFT**+**alt**+**F7** `Window.PreviousDocumentWindowNav` ve **alt**+**F7** 0 ' a atar.

> [!NOTE]
> Kullandığınız ayarlar birleşimine bu komuta atanmış kısayol tuşu birleşimi zaten yoksa, **Seçenekler** Iletişim kutusunun **klavye** sayfasını kullanarak kendi özel komutunuzu atayabilirsiniz. Daha fazla bilgi için bkz. [klavye kısayollarını tanımlamak ve özelleştirmek](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

### <a name="to-switch-to-a-specific-tool-window-in-the-ide"></a>IDE 'de belirli bir araç penceresine geçiş yapmak için

- **IDE Gezginini**göstermek için **alt**+**F7** tuşuna basın. Geçiş yapmak istediğiniz pencereyi seçene kadar **alt** tuşunu basılı tutun ve **F7** tuşuna basın.

    > [!TIP]
    > **Etkin araç pencereleri** listesinden gittiğiniz sırayı tersine çevirmek için **SHIFT**+**alt** tuşlarını basılı tutun ve **F7**tuşuna basın.

## <a name="see-also"></a>Ayrıca bkz.

- [Pencere düzenlerini özelleştirme](../ide/customizing-window-layouts-in-visual-studio.md)
- [Varsayılan klavye kısayolları](../ide/default-keyboard-shortcuts-in-visual-studio.md)