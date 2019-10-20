---
title: Başlangıç zamanını iyileştirme | Microsoft Docs
ms.date: 11/15/2016
ms.topic: conceptual
helpviewer_keywords:
- startup time [Visual Studio]
- optimizing startup time [Visual Studio]
- speed up start time [Visual Studio]
ms.assetid: d1508121-8499-4084-8eb5-fa89fa7b17d3
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0f00bbc7741768852b5928b249dc7035bc440992
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670395"
---
# <a name="optimize-visual-studio-startup-time"></a>Visual Studio Başlangıç Süresini İyileştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

İdeal olarak, Visual Studio her zaman mümkün olduğunca hızlı bir şekilde başlamalıdır. Ancak, Visual Studio uzantıları ve açık araç pencereleri başlangıçta otomatik olarak yüklendiklerinden başlangıç süresini olumsuz etkileyebilir. **Visual Studio performansını Yönet** penceresi, Visual Studio başlangıç zamanını yalnızca hangi uzantıların ve özelliklerin etkilediğini görmenize imkan tanır, ancak aynı zamanda, Visual Studio 'nun ne kadar hızlı bir şekilde başlayacağını daha fazla denetleyebilmeniz için yükleme davranışlarını belirlemenizi sağlar.

## <a name="control-startup-behavior"></a>Denetim başlatma davranışı

Başlangıç zamanını genişletmemek için, Visual Studio 2017 ve üzeri, istek üzerine yükleme yaklaşımını kullanarak başlangıç sırasında uzantıları yüklemeyi önleyin. Bu, uzantıların Visual Studio başladıktan hemen sonra açılmayacağı, ancak başlangıçta zaman uyumsuz olarak bir başlangıç sonrasında açılmayacağı anlamına gelir. Ayrıca, önceki bir Visual Studio oturumunda açık olan araç pencereleri başlangıç süresini yavaşlatabileceğinden, Visual Studio başlangıç süresini etkilememek için araç pencerelerini daha akıllı bir şekilde açar.

Visual Studio yavaş başlangıç algılarsa, yavaşlamaya neden olan uzantı veya araç penceresine uyarı veren bir açılır ileti görüntülenir. İleti ayrıca, başlangıç performansını etkileyen Uzantılar ve araçlar pencerelerini listeleyen **Visual Studio performansını Yönet** iletişim kutusu için bir bağlantı sağlar. Bu iletişim kutusu, başlangıç performansını geliştirmek için uzantı ve araç penceresi ayarlarını değiştirmenize olanak sağlar.

![Visual Studio performansını yönetme-açılan pencere](../ide/media/vside-perfdialog-popup.PNG "Visual Studio performansını yönetme-açılan pencere")

**Visual Studio performansını Yönet** iletişim kutusunun iki kategorisi vardır: **Uzantılar** ve **araç pencereleri**.

### <a name="control-extensions"></a>Denetim uzantıları
Bir uzantı Visual Studio başlangıcını yavaşlattığı zaman uzantı türlerinden birini seçtiğinizde uzantı **Visual Studio performansını Yönet iletişim** kutusunda görünür. Başlangıç saati ( **etki** bölümü altında listelenmiştir) üzerindeki etki, kabul edilemeyecek kadar yüksekse, **devre dışı bırak** düğmesini seçerek uzantıyı başlangıçta her zaman devre dışı bırakmayı seçebilirsiniz. Uzantı Yöneticisi veya Visual Studio performansını Yönet iletişim kutusunu kullanarak, gelecekteki oturumların uzantısını yeniden etkinleştirebilirsiniz.

![Visual Studio performansı-uzantıları yönetme](../ide/media/vside-perfdialog-extensions.PNG "Visual Studio performansı-uzantıları yönetme")

Başlangıç uzantılarına ek olarak, çözüm yüklenirken yüklenen uzantıları da devre dışı bırakabilir veya bir Kullanıcı ne zaman tür. İlişkili uzantıların bir listesini görmek için senaryoyu seçmeniz yeterlidir.

### <a name="control-tool-windows"></a>Denetim Aracı pencereleri
Bir araç penceresi Visual Studio başlangıcını yavaşlattığı takdirde, varsayılan davranışından bırakmayı seçebilirsiniz (başlangıç hızında herhangi bir avantaj elde edebilirsiniz) veya iki davranıştan birini seçerek davranışını geçersiz kılabilirsiniz:

- **Başlangıçta pencere gösterme:** Bu seçeneği belirlerseniz, önceki bir oturumda açık bırakılmış olsa bile, Visual Studio 'Yu açtığınızda belirtilen araç penceresi her zaman kapatılacak. Menüden araç penceresini açabilirsiniz.
- **Başlangıçta pencereyi otomatik gizle:** Bir araç penceresi önceki bir oturumda açık bırakılmış ise, bu seçeneğin belirlenmesi araç penceresinin başlatılmasını önlemek için başlangıçta araç penceresinin grubunu daraltabilir. Araç penceresi hala kullanılabilir olduğundan, ancak artık Visual Studio başlangıç zamanını olumsuz şekilde etkilemediğinden, bu bir araç penceresini sık kullanıyorsanız bu iyi bir seçenektir.

![Visual Studio performansı yönetme-araç pencereleri](../ide/media/vside-perfdialog-toolwindows.PNG "Visual Studio performansı yönetme-araç pencereleri")

Daha sonra fikrinizi değiştirirseniz, **Visual Studio performansını Yönet** iletişim kutusunda bu seçeneklerden herhangi birini döndürebilirsiniz. **Visual Studio performansını Yönet** iletişim kutusunu açmak için, menü çubuğunda **Yardım**, **Visual Studio performansını Yönet**' i seçin.
