---
title: Visual Studio SDK 'sını yükleme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: visual-studio-sdk
ms.topic: conceptual
ms.assetid: c730edb6-5099-4c16-85a8-08def09f1455
caps.latest.revision: 4
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 88a6266a3f5910def0bf5041a37f89c2b3d67416
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64858693"
---
# <a name="installing-the-visual-studio-sdk"></a>Visual Studio SDK’yı Yükleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 2015 ' den başlayarak, Visual Studio SDK 'sını indirme merkezinden yüklememeyin. Visual Studio kurulumuna isteğe bağlı bir özellik olarak dahildir. VS SDK ' yı daha sonra da yükleyebilirsiniz.  
  
## <a name="installing-the-visual-studio-sdk-as-part-of-a-visual-studio-installation"></a>Visual Studio SDK 'sını bir Visual Studio yüklemesinin parçası olarak yükleme  
 Visual Studio yüklemenize VSSDK eklemek istiyorsanız, özel bir yükleme yapmanız gerekir.  
  
> [!NOTE]
> Yükleme yürütülebilir dosyasında, Visual Studio SDK **Visual Studio genişletilebilirlik Araçları**olarak adlandırılır.  
  
1. Visual Studio 2015 yüklemesini başlatın. Visual Studio 'nun herhangi bir sürümünü Express dışında yükleyebilirsiniz.  
  
2. İlk ekranda **varsayılan**değil, **özel**' i seçin. **İleri**’ye tıklayın.  
  
3. Özel özelliklerin ağaç görünümünü görmeniz gerekir. **Ortak araçları**açın. **Visual Studio genişletilebilirlik Araçları** görmeniz gerekir.  
  
     ![Vssdkınstall](../extensibility/media/vssdkinstall.png "Vssdkınstall")  
  
4. **Visual Studio genişletilebilirlik Araçları** işaretleyin ve ardından **İleri** ' ye tıklayın ve yüklemeye devam edin.  
  
## <a name="installing-the-visual-studio-sdk-after-installing-visual-studio"></a>Visual Studio 'yu yükledikten sonra Visual Studio SDK 'sını yükleme  
 Visual Studio yüklemesini tamamladıktan sonra Visual Studio SDK 'yı yüklemeye karar verirseniz, aşağıdaki yordamı izlemeniz gerekir:  
  
1. **Denetim Masası/Programlar/Programlar ve Özellikler**' e gidin ve **Visual Studio 2015**' i arayın. Visual Studio 2015 ' in her türlü sürümü için Visual Studio SDK 'sını Express dışında yükleyebilirsiniz.  
  
2. **Visual Studio 2015**öğesine sağ tıklayın ve ardından **Değiştir**' e tıklayın. Yükleme sayfasını görmeniz gerekir.  
  
3. Yukarıdaki **bir Visual Studio yüklemesinin parçası olarak Visual Studio SDK 'Yı yükleme** ile aynı yordamı izleyin.  
  
4. Visual Studio SDK 'yı yüklemek için **Visual Studio genişletilebilirlik Araçları** bağlantısına tıklayın.  
  
## <a name="installing-the-visual-studio-sdk-from-a-solution"></a>Bir çözümden Visual Studio SDK 'sını yükleme  
 Önce VSSDK 'yi yüklemeden bir genişletilebilirlik projesiyle bir çözüm açarsanız, Çözüm Gezgini üzerinde vurgulanan bir bilgi çubuğu istenir. Aşağıdakine benzer şekilde görünmelidir:  
  
 ![SolutionExplorerInstall](../extensibility/media/solutionexplorerinstall.png "SolutionExplorerInstall")  
  
## <a name="installing-the-visual-studio-sdk-from-the-command-line"></a>Komut satırından Visual Studio SDK 'sını yükleme  
 **/InstallSelectableItems** anahtarını Visual Studio yükleyicisi ile birlikte kullanarak, VSSDK 'yi komut satırından yükleyebilirsiniz. Yükleyici ile komut satırı parametrelerini kullanma hakkında ayrıntılı bilgi için bkz. [Visual Studio 2015 'Yi yükleme](../install/install-visual-studio-2015.md).  
  
 Aşağıda, Visual Studio 2015 Community yükleyicisi kullanılarak VSSDK sessizce nasıl yükleneceğine yer verilmiştir:  
  
```  
vs_community.exe /s /installSelectableItems VS_SDK_GROUPV1  
```  
  
 Visual Studio 'nun yüklü sürümü ile eşleşen Visual Studio yükleyicisini kullanmanız gerektiğini unutmayın. Örneğin, bilgisayarınızda yüklü Visual Studio Enterprise yüklüyse, Visual Studio Enterprise yükleyiciyi (vs_enterprise.exe) çalıştırmanız gerekir.
