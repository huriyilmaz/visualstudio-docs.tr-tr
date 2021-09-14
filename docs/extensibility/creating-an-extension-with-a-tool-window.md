---
title: Araç Penceresi Ile Uzantı Oluşturma | Microsoft Docs
description: VsIX proje şablonunu ve Özel Araç Penceresi öğe şablonunu kullanarak bir araç penceresiyle uzantı oluşturma hakkında bilgi edinebilirsiniz.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627681"
---
# <a name="create-an-extension-with-a-tool-window"></a>Araç penceresiyle uzantı oluşturma

Bu yordamda VSIX proje şablonunu ve Özel  Araç Penceresi öğe şablonunu kullanarak bir araç penceresiyle uzantı oluşturma hakkında bilgi edinebilirsiniz.

## <a name="prerequisites"></a>Önkoşullar

 2015'Visual Studio başlayarak, Visual Studio SDK'yı indirme merkezinden yüklemezsiniz. Bu, kurulumda isteğe bağlı bir Visual Studio olarak dahil edilir. VS SDK'yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için [bkz. Visual Studio SDK'sı yükleme.](../extensibility/installing-the-visual-studio-sdk.md)

### <a name="create-a-tool-window"></a>Araç penceresi oluşturma

1. **FirstWindow** adlı bir VSIX projesi oluşturun. VSIX proje şablonunu New **Project** iletişim kutusunda "vsix" ifadesini arayarak bulabilirsiniz.

2. Proje **açıldığında, MyWindow** adlı bir araç penceresi öğesi şablonu ekleyin. Giriş **Çözüm Gezgini** proje düğümüne sağ tıklayın ve Yeni Öğe **Ekle'yi**  >  **seçin.** Yeni Öğe **Ekle iletişim kutusunda** Visual **C#**  >  **Genişletilebilirliği'ne** gidin ve Özel Araç **Penceresi'ne tıklayın.** Pencerenin **en** altındaki Ad alanında, araç penceresi dosya adını *MyWindow.cs olarak değiştirebilirsiniz.*

3. Projeyi derleme ve hata ayıklamayı başlatma.

   Deneysel örnek Visual Studio görünür. Deneysel örnek hakkında daha fazla bilgi için [bkz. Deneysel örneği.](../extensibility/the-experimental-instance.md)

4. Deneysel örnekte Diğer Örnekleri   >  **Görüntüle'ye Windows.**

   **MyWindow** için bir menü öğesi görüyor gerekir. Tıklayın.

   **MyWindow** başlığına sahip bir araç penceresi ve Bana Tıklayın! düğmesini **görüyor gerekir.**
