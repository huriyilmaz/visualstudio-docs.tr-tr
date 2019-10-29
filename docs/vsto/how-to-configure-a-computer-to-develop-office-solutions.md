---
title: 'Nasıl yapılır: Office çözümleri geliştirmek için bir bilgisayarı yapılandırma'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- prerequisites [Office development in Visual Studio]
- Office development in Visual Studio, installing tools
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: eb29dc4151bc457eb60ce836986817bc1b0137c9
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985957"
---
# <a name="how-to-configure-a-computer-to-develop-office-solutions"></a>Nasıl yapılır: Office çözümleri geliştirmek için bir bilgisayarı yapılandırma
  Visual Studio 'da Microsoft Office geliştirici araçları 'nı kullanabilmeniz için bir geliştirme bilgisayarı yapılandırmak için bu konudaki yönergeleri izleyin. Bu adımları gerçekleştirmek için geliştirme bilgisayarında yönetici ayrıcalıklarına sahip olmanız gerekir.

### <a name="to-configure-the-development-computer"></a>Geliştirme bilgisayarını yapılandırmak için

1. Visual Studio 'nun Office geliştirici araçlarını içeren bir sürümünü yükler. Office geliştirici araçları varsayılan olarak yüklenir. Yüklenecek özellikleri seçerek Visual Studio yüklemesini özelleştirirseniz, kurulum sırasında **Microsoft Office geliştirici araçları** seçildiğinden emin olun. Office geliştirici araçlarını içeren Visual Studio sürümleri hakkında daha fazla bilgi için bkz. [Office çözümleri geliştirmek için bir bilgisayarı yapılandırma](../vsto/configuring-a-computer-to-develop-office-solutions.md).

2. Visual Studio 'da Office geliştirici araçları tarafından desteklenen bir Office sürümünü yükler. Daha fazla bilgi için bkz. [Office çözümleri geliştirmek için bir bilgisayarı yapılandırma](../vsto/configuring-a-computer-to-develop-office-solutions.md).

     Yüklediğiniz Office sürümü için de PIA 'leri yüklediğinizden emin olun. PIA 'ler varsayılan olarak Office ile yüklenir. Office kurulumunu değiştirirseniz hedeflemek istediğiniz uygulamalar için **.NET programlama desteği** özelliğinin seçildiğinden emin olun.

3. Visual Studio 'nun Ingilizce sürümüne sahipseniz ancak Windows için Ingilizce olmayan ayarları kullanıyorsanız, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] iletilerini Windows ile aynı dilde görmek için [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] dil paketini yükleyebilirsiniz. Visual Studio 'nun Ingilizce olmayan sürümleri dil paketini otomatik olarak yükler. Dil paketi [Microsoft İndirme Merkezi](https://www.microsoft.com/download/details.aspx?id=54246)' nden edinilebilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio &#40;'da Office geliştirme ile çalışmaya başlama&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Nasıl yapılır: Office çalışma zamanı yeniden dağıtılabilir için Visual Studio Araçları yüklemesi](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)
- [Nasıl yapılır: Office birincil birlikte çalışma derlemelerini yüklemek](../vsto/how-to-install-office-primary-interop-assemblies.md)
