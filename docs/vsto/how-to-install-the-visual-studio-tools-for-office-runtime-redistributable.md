---
title: 'Nasıl Yapılır: Office Çalışma Zamanı Yeniden Dağıtılabilir için Visual Studio Araçları Yükleme'
description: Office çalışma zamanı yeniden dağıtılabilir için Microsoft Visual Studio 2010 araçlarını nasıl yükleyebileceğinizi öğrenin.
titleSuffix: ''
ms.date: 01/25/2022
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office runtime [Office development in Visual Studio]
- installing Office development tools in Visual Studio
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.custom: devdivchpfy22
ms.openlocfilehash: 40851fbcb1856176ad571c65bfde741e99b7fd82
ms.sourcegitcommit: 23b0ef3815833426933ff6491271034658683f9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/02/2022
ms.locfileid: "137983846"
---
# <a name="how-to-install-the-visual-studio-tools-for-office-runtime-redistributable"></a>Nasıl Yapılır: Office Çalışma Zamanı Yeniden Dağıtılabilir için Visual Studio Araçları Yükleme

   içinde [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Visual Studio kullanılarak oluşturulan çözümleri çalıştıran her bilgisayar, Office çalışma zamanına yönelik Visual Studio 2010 araçlarını yüklemelidir. Çalışma zamanı, yüklediğinizde [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ve Microsoft Office otomatik olarak yüklenir. daha fazla bilgi için bkz. [Office için Visual Studio Araçları runtime yükleme senaryoları](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md).

[!include[Add-ins note](includes/addinsnote.md)]

 Aşağıdaki durumlarda el ile yükleme yönergelerini izlemeniz gerekebilir:

- ' Nı bir sunucusuna yüklemeniz [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] gerekir.

- çalışma zamanını, Office çözümleri için diğer tüm önkoşulların zaten yüklü olduğu bir bilgisayara yüklemeniz gerekir.

    > [!NOTE]
    > .NET Framework ve ' [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] ü yüklemek için geliştirme bilgisayarında bir yönetici olmanız gerekir.

## <a name="to-install-the-visual-studio-tools-for-office-runtime"></a>Office için Visual Studio Araçları çalışma zamanını yüklemek için

1. [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]Veya sonraki sürümünü yükler.

    - indirmek [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] için bkz. [Microsoft .NET Framework 4 (Web yükleyicisi)](https://www.microsoft.com/download/details.aspx?id=17851).

    - indirmek [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)] için bkz. [Microsoft .NET Framework 4 istemci profili (Web yükleyicisi)](https://www.microsoft.com/download/details.aspx?id=17113).

    - indirmek [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] için bkz. [Microsoft .NET Framework 4,5](https://www.microsoft.com/download/details.aspx?id=30653).

2. Uygulamasını yüklemek [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] için *vstor_redist.exe* çalıştırın.

     bu kurulum dosyalarını, [Office çalışma zamanına yönelik Visual Studio 2010 araçlarından](https://www.microsoft.com/download/details.aspx?id=56961)indirebilirsiniz. İçin [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] önkoşulları, .NET Framework önkoşulları ile eşleşir.

     , [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Dil paketlerini içerir. Windows yüklemeniz ingilizce dışında bir dile ayarlandıysa, çalışma zamanı iletilerini Windows kullandığınız dilde görüntüleyebilirsiniz. Benzer şekilde, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] öğesini yüklerseniz. ardından çözümlerinizi ingilizce dışındaki bir dilde Windows yüklemelerinde çalıştırın, çalışma zamanı iletileri Windows aynı dilde görünür. Bazı durumlarda, daha fazla dil paketine ihtiyacınız bulunabilir. örneğin, Windows kopyanız birden fazla dil ayarı kullanıyorsa, ek dil paketlerine ihtiyacınız bulunabilir. Alternatif olarak, ' yi zaten [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] yükledikten sonra başka bir dile geçiş yapabilirsiniz. dil paketlerini [Microsoft Office sistemi (sürüm 4,0 çalışma zamanı) dil paketi için Microsoft Visual Studio 2010 araçlarında](https://www.microsoft.com/download/details.aspx?id=54246)bulabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio &#40;Office geliştirmeye başlayın&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Office çözümleri geliştirmek için bir bilgisayarı yapılandırma](../vsto/configuring-a-computer-to-develop-office-solutions.md)
- [nasıl yapılır: Office çözümleri geliştirmek için bir bilgisayarı yapılandırma](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)
- [nasıl yapılır: birincil birlikte çalışma derlemelerini Office yüklemesi](../vsto/how-to-install-office-primary-interop-assemblies.md)
- [ServerDocument sınıfını kullanarak bir sunucudaki belgeleri yönetme](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)
- [Office çözümünü dağıtma](../vsto/deploying-an-office-solution.md)
