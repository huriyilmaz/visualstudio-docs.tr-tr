---
title: 'Nasıl yapılır: Office çözümleri geliştirmek için bir bilgisayarı yapılandırma'
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 3b13aa65e4dd5868a36e0dd833351b1d1751d8b0
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546178"
---
# <a name="how-to-configure-a-computer-to-develop-office-solutions"></a>Nasıl yapılır: Office çözümleri geliştirmek için bir bilgisayarı yapılandırma
  Visual Studio 'da Microsoft Office geliştirici araçları 'nı kullanabilmeniz için bir geliştirme bilgisayarı yapılandırmak için bu konudaki yönergeleri izleyin. Bu adımları gerçekleştirmek için geliştirme bilgisayarında yönetici ayrıcalıklarına sahip olmanız gerekir.

### <a name="to-configure-the-development-computer"></a>Geliştirme bilgisayarını yapılandırmak için

1. Visual Studio 'nun Office geliştirici araçlarını içeren bir sürümünü yükler. Office geliştirici araçları varsayılan olarak yüklenir. Yüklenecek özellikleri seçerek Visual Studio yüklemesini özelleştirirseniz, kurulum sırasında **Microsoft Office geliştirici araçları** seçildiğinden emin olun. Office geliştirici araçlarını içeren Visual Studio sürümleri hakkında daha fazla bilgi için bkz. [Office çözümleri geliştirmek için bir bilgisayarı yapılandırma](../vsto/configuring-a-computer-to-develop-office-solutions.md).

2. Visual Studio 'da Office geliştirici araçları tarafından desteklenen bir Office sürümünü yükler. Daha fazla bilgi için bkz. [Office çözümleri geliştirmek için bir bilgisayarı yapılandırma](../vsto/configuring-a-computer-to-develop-office-solutions.md).

     Yüklediğiniz Office sürümü için de PIA 'leri yüklediğinizden emin olun. PIA 'ler varsayılan olarak Office ile yüklenir. Office kurulumunu değiştirirseniz hedeflemek istediğiniz uygulamalar için **.NET programlama desteği** özelliğinin seçildiğinden emin olun.

3. Visual Studio 'nun Ingilizce sürümüne sahipseniz ancak Windows için Ingilizce olmayan ayarları kullanıyorsanız, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Windows ile aynı dildeki iletileri görmek için dil paketini yükleyebilirsiniz. Visual Studio 'nun Ingilizce olmayan sürümleri dil paketini otomatik olarak yükler. Dil paketi [Microsoft İndirme Merkezi](https://www.microsoft.com/download/details.aspx?id=54246)' nden edinilebilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 'da Office geliştirme &#40;kullanmaya başlama&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Nasıl yapılır: Office çalışma zamanı yeniden dağıtılabilir için Visual Studio Araçları yüklemesi](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)
- [Nasıl yapılır: Office birincil birlikte çalışma derlemelerini yüklemek](../vsto/how-to-install-office-primary-interop-assemblies.md)
