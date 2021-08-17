---
title: Araç penceresi ile uzantı oluşturma | Microsoft Docs
description: Bir araç penceresi ile uzantı oluşturmak için VSıX proje şablonunu ve özel araç penceresi öğesi şablonunu nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 3/16/2019
ms.topic: how-to
ms.assetid: 585b0a3a-f85b-4f92-81bb-9ca499bb8a89
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: cde02a72f180fa497c599c661f12c4d279a3e1ba
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122073506"
---
# <a name="create-an-extension-with-a-tool-window"></a>Araç penceresi ile uzantı oluşturma

Bu yordamda, bir araç penceresi ile uzantı oluşturmak için VSıX proje şablonunu ve **özel araç penceresi** öğesi şablonunu nasıl kullanacağınızı öğrenirsiniz.

## <a name="prerequisites"></a>Önkoşullar

 Visual Studio 2015 ' den başlayarak, Visual Studio SDK 'sını indirme merkezi ' nden yüklemeyin. Visual Studio kurulum 'da isteğe bağlı bir özellik olarak eklenmiştir. VS SDK ' yı daha sonra da yükleyebilirsiniz. daha fazla bilgi için bkz. [Visual Studio SDK 'yı ınstall](../extensibility/installing-the-visual-studio-sdk.md).

### <a name="create-a-tool-window"></a>Araç penceresi oluşturma

1. **Firstwindow** ADLı bir VSIX projesi oluşturun. vsıx proje şablonunu, **yeni Project** iletişim kutusunda "vsıx" arayarak bulabilirsiniz.

2. Proje açıldığında, **MyWindow** adlı bir araç penceresi öğe şablonu ekleyin. **Çözüm Gezgini**, proje düğümüne sağ tıklayın ve   >  **Yeni öğe** Ekle ' yi seçin. **Yeni öğe Ekle** iletişim kutusunda, **Visual C#**  >  **genişletilebilirliği** ' ne gidin ve **özel araç penceresi**' ni seçin. Pencerenin alt kısmındaki **ad** alanında araç penceresi dosya adını *MyWindow. cs* olarak değiştirin.

3. Projeyi derleyin ve hata ayıklamayı başlatın.

   Visual Studio deneysel örneği görüntülenir. Deneysel örnek hakkında daha fazla bilgi için bkz. [deneysel örnek](../extensibility/the-experimental-instance.md).

4. deneysel örnekte,   >  **diğer Windows** görüntüle ' ye gidin.

   **MyWindow** için bir menü öğesi görmeniz gerekir. Tıklayın.

   **MyWindow** başlığına ve **bana tıkladığını** belirten bir düğmeye sahip bir araç penceresi görmeniz gerekir.
