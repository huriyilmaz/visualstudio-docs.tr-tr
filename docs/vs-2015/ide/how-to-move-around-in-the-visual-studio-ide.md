---
title: "Nasıl yapılır: IDE 'de gezinme | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
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
caps.latest.revision: 33
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 89c4447eb6bbc4b2ae9f7667672626d5119c61d6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651791"
---
# <a name="how-to-move-around-in-the-visual-studio-ide"></a>Nasıl Yapılır: Visual Studio IDE’de Gezinme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tümleşik geliştirme ortamı (IDE), tercihlerinize veya proje gereksinimlerinize bağlı olarak, pencereden pencereye ve dosyaya farklı yollarla dosya taşımanıza olanak tanımak üzere tasarlanmıştır. Düzenleyicideki açık dosyalar arasında dolaşmayı veya IDE 'deki tüm etkin araç pencerelerini kullanarak geçiş yapabilirsiniz. Ayrıca, son erişildiği sırada ne olursa olsun, düzenleyicide açık olan herhangi bir dosyaya doğrudan geçiş yapabilirsiniz. Bu özellikler, IDE 'de çalışırken üretkenliğinizi artırmaya yardımcı olabilir.

> [!NOTE]
> İletişim kutularında kullanılabilen seçenekler ve gördüğünüz menü komutlarının adları ve konumları, etkin ayarlarınıza veya sürümüne bağlı olarak yardım altında açıklananlar arasından farklılık gösterebilir. Bu yardım sayfası, **genel geliştirme ayarları** göz önünde bulundurularak yazılmıştır. Ayarlarınızı değiştirmek için **Araçlar** menüsünden **Içeri ve dışarı aktarma ayarları** ' nı seçin. Daha fazla bilgi için bkz. [Visual Studio 'Da geliştirme ayarlarını özelleştirme](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="keyboard-shortcuts"></a>Klavye Kısayolları
 Visual Studio 'daki neredeyse her menü komutunun bir klavye kısayolu vardır. Kendi özel kısayollarınızı da oluşturabilirsiniz. Daha fazla bilgi için bkz. [klavye kısayollarını tanımlama ve özelleştirme](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

## <a name="navigating-among-files-in-the-editor"></a>Düzenleyicide dosyalar arasında gezinme
 Düzenleyicide açık olan dosyalar arasında gezinmek için çeşitli yöntemler kullanabilirsiniz. Dosyalara erişmek istediğiniz sıraya göre dosyalar arasında geçiş yapabilirsiniz, daha önce açık olan herhangi bir dosyayı hızlı bir şekilde bulmak için IDE gezginini kullanın veya her zaman görünür olmaları için sık kullanılan dosyaları sekmeye uygun olarak sabitleyin.

 Geriye doğru ilerleyin ve Microsoft Internet Explorer 'da görüntüleme geçmişiniz için, geri ve Ileri ' ye benzer şekilde, düzenleyicide bulunan açık dosyalar üzerinden Ileri döngülerine gidin.

#### <a name="to-move-through-open-files-in-order-of-use"></a>Açık dosyalar aracılığıyla kullanım sırasıyla geçiş yapmak için

- Açık belgeleri en son dokundukları sırada etkinleştirmek için CTRL + EKSI IŞARETI ' ne basın.

- Açık belgeleri ters sırada etkinleştirmek için CTRL + SHIFT + eksı IŞARETINE basın.

  > [!NOTE]
  > **Geriye giderek** **İleri** git **Görünüm** menüsünde de bulunabilir.

  Ayrıca, dosyaya son erişiminizden bağımsız olarak, **IDE Gezginini**, düzenleyicide **etkin dosyalar** listesini veya **Windows** iletişim kutusunu kullanarak, düzenleyicide açık olan belirli bir dosyaya geçiş yapabilirsiniz.

  **IDE Gezgini** , Windows uygulama değiştiricisinden çok benzer şekilde çalışmaktadır. Menülerden kullanılamaz ve yalnızca kısayol tuşları kullanılarak erişilebilir. **IDE Gezginine** erişmek için iki komuttan birini kullanabilirsiniz (aşağıda gösterildiği gibi), üzerinde geçiş yapmak istediğiniz sıraya bağlı olarak dosyalar arasında geçiş yapmak için iki komuttan yararlanabilirsiniz.

  ![Visual Studio IDE Gezgini](../ide/media/vs2015-ide-navigator.png "VS2015_IDE_Navigator")

  `Window.PreviousDocumentWindowNav` en son erişilen dosyaya taşımanızı sağlar ve `Window.NextDocumentWindowNav` ters sırada taşımanızı sağlar. Genel geliştirme ayarları, CTRL + SHIFT + TAB tuşlarına `Window.PreviousDocumentWindowNav` ve CTRL + TAB öğesine atar `Window.NextDocumentWindowNav` .

> [!NOTE]
> Kullandığınız ayarlar birleşimine bu komuta atanmış kısayol tuşu birleşimi zaten yoksa, **Seçenekler** Iletişim kutusunun **klavye** sayfasını kullanarak kendi özel komutunuzu atayabilirsiniz. Daha fazla bilgi için bkz. [klavye kısayollarını tanımlama ve özelleştirme](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

#### <a name="to-switch-to-specific-files-in-the-editor"></a>Düzenleyicideki belirli dosyalara geçiş yapmak için

- **IDE Gezginini**göstermek için CTRL + TAB tuşlarına basın. CTRL tuşunu basılı tutun ve geçiş yapmak istediğiniz dosyayı seçene kadar SEKME tuşuna basın.

    > [!TIP]
    > **Etkin dosyalar** listesinden gittiğiniz sırayı tersine ÇEVIRMEK için CTRL + SHIFT tuşlarını basılı tutarak Tab tuşuna basın.

     \- veya

- Düzenleyicinin sağ üst köşesinde **etkin dosyalar** düğmesini seçin ve ardından listeden bir dosyayı seçerek geçiş yapın.

     \- veya

- Menü çubuğunda, **pencere**, **Windows**' u seçin.

- Listede, görüntülemek istediğiniz dosyayı seçin ve ardından **Etkinleştir**' i seçin.

## <a name="navigating-among-tool-windows-in-the-ide"></a>IDE 'deki araç pencereleri arasında gezinme
 **IDE Gezgini** , IDE 'de açtığınız araç pencereleri arasında geçiş yapmanızı de sağlar. **IDE Gezginine** erişmek için iki komuttan birini kullanarak, geçiş yapmak istediğiniz sıraya bağlı olarak araç pencereleri arasında geçiş yapabilirsiniz. `Window.PreviousToolWindowNav` en son erişilen dosyaya taşımanızı sağlar ve `Window.NextToolWindowNav` ters sırada taşımanızı sağlar. Genel geliştirme ayarları SHIFT + ALT + F7 öğesine `Window.PreviousDocumentWindowNav` ve alt + F7 'e atar `Window.NextDocumentWindowNav` .

> [!NOTE]
> Kullandığınız ayarlar birleşimine bu komuta atanmış kısayol tuşu birleşimi zaten yoksa, **Seçenekler** Iletişim kutusunun **klavye** sayfasını kullanarak kendi özel komutunuzu atayabilirsiniz. Daha fazla bilgi için bkz. [klavye kısayollarını tanımlama ve özelleştirme](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

#### <a name="to-switch-to-a-specific-tool-window-in-the-ide"></a>IDE 'de belirli bir araç penceresine geçiş yapmak için

- **IDE Gezginini**göstermek için Alt + F7 tuşlarına basın. Geçiş yapmak istediğiniz pencereyi seçene kadar ALT tuşunu basılı tutun ve F7 tuşuna basın.

    > [!TIP]
    > **Etkin araç pencereleri** listesinden gittiğiniz sırayı tersine ÇEVIRMEK için SHIFT + alt tuşlarını basılı tutun ve F7 tuşuna basın.

## <a name="see-also"></a>Ayrıca Bkz.
 [Pencere düzenlerini özelleştirme](../ide/customizing-window-layouts-in-visual-studio.md) [varsayılan klavye kısayolları](../ide/default-keyboard-shortcuts-in-visual-studio.md)
