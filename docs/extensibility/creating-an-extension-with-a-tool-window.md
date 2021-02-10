---
title: Araç penceresi ile uzantı oluşturma | Microsoft Docs
description: Bir araç penceresi ile uzantı oluşturmak için VSıX proje şablonunu ve özel araç penceresi öğesi şablonunu nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 3/16/2019
ms.topic: how-to
ms.assetid: 585b0a3a-f85b-4f92-81bb-9ca499bb8a89
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1b03b7a4941609462fca27bebf67d8ad2a8f7044
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99944927"
---
# <a name="create-an-extension-with-a-tool-window"></a>Araç penceresi ile uzantı oluşturma

Bu yordamda, bir araç penceresi ile uzantı oluşturmak için VSıX proje şablonunu ve **özel araç penceresi** öğesi şablonunu nasıl kullanacağınızı öğrenirsiniz.

## <a name="prerequisites"></a>Önkoşullar

 Visual Studio 2015 ' den başlayarak, Visual Studio SDK 'sını indirme merkezinden yüklememeyin. Visual Studio kurulumuna isteğe bağlı bir özellik olarak dahildir. VS SDK ' yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için bkz. [Visual Studio SDK 'Yı yüklemeyi](../extensibility/installing-the-visual-studio-sdk.md).

### <a name="create-a-tool-window"></a>Araç penceresi oluşturma

1. **Firstwindow** ADLı bir VSIX projesi oluşturun. "VSIX" araması yaparak VSıX proje şablonunu **Yeni proje** iletişim kutusunda bulabilirsiniz.

2. Proje açıldığında, **MyWindow** adlı bir araç penceresi öğe şablonu ekleyin. **Çözüm Gezgini**, proje düğümüne sağ tıklayın ve   >  **Yeni öğe** Ekle ' yi seçin. **Yeni öğe Ekle** iletişim kutusunda, **Visual C#**  >  **genişletilebilirliği** ' ne gidin ve **özel araç penceresi**' ni seçin. Pencerenin alt kısmındaki **ad** alanında araç penceresi dosya adını *MyWindow.cs* olarak değiştirin.

3. Projeyi derleyin ve hata ayıklamayı başlatın.

   Visual Studio 'nun deneysel örneği görüntülenir. Deneysel örnek hakkında daha fazla bilgi için bkz. [deneysel örnek](../extensibility/the-experimental-instance.md).

4. Deneysel örnekte,   >  **diğer pencereleri** görüntüle ' ye gidin.

   **MyWindow** için bir menü öğesi görmeniz gerekir. Tıklayın.

   **MyWindow** başlığına ve **bana tıkladığını** belirten bir düğmeye sahip bir araç penceresi görmeniz gerekir.
