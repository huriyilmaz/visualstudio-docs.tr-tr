---
title: Araç penceresi ile uzantı oluşturma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 585b0a3a-f85b-4f92-81bb-9ca499bb8a89
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 94c8335b8d723ef20c04cfffe6b3788d71ecaa4f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62431855"
---
# <a name="creating-an-extension-with-a-tool-window"></a>Araç Penceresi İçeren Bir Uzantı Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu yordamda, bir araç penceresi ile uzantı oluşturmak için VSıX proje şablonunu ve **özel araç penceresi** öğesi şablonunu nasıl kullanacağınızı öğrenirsiniz.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Visual Studio 2015 ' den başlayarak, Visual Studio SDK 'sını indirme merkezinden yüklememeyin. Visual Studio kurulumuna isteğe bağlı bir özellik olarak dahildir. VS SDK ' yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için bkz. [Visual Studio SDK 'Yı yükleme](../extensibility/installing-the-visual-studio-sdk.md).  
  
### <a name="creating-a-tool-window"></a>Araç penceresi oluşturma  
  
1. **Firstwindow**ADLı bir VSIX projesi oluşturun. VSıX proje şablonunu, **Visual C#/genişletilebilirlik**altında **Yeni proje** iletişim kutusunda bulabilirsiniz.  
  
2. Proje açıldığında, **firstwindow**adlı bir araç penceresi öğe şablonu ekleyin. **Çözüm Gezgini**, proje düğümüne sağ tıklayın ve **Ekle/yeni öğe**' yi seçin. **Yeni öğe Ekle** iletişim kutusunda, **Visual C#/genişletilebilirlik** ' e gidin ve **özel araç penceresi**' ni seçin. Pencerenin alt kısmındaki **ad** alanında araç penceresi dosya adını **FirstWindow.cs**olarak değiştirin.  
  
3. Projeyi derleyin ve hata ayıklamayı başlatın.  
  
     Visual Studio 'nun deneysel örneği görüntülenir. Deneysel örnek hakkında daha fazla bilgi için bkz. [deneysel örnek](../extensibility/the-experimental-instance.md).  
  
4. Deneysel örnekte, **Görünüm/diğer pencereler**' e gidin.  
  
     **Firstwindow**için bir menü öğesi görmeniz gerekir. Tıklayın.  
  
     **Firstwindow** başlığına ve **bana tıkladığını** belirten bir düğmeye sahip bir araç penceresi görmeniz gerekir.
