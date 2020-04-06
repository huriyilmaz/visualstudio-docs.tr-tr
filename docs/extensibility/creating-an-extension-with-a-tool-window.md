---
title: Araç Penceresi ile Uzantı Oluşturma | Microsoft Dokümanlar
ms.date: 3/16/2019
ms.topic: conceptual
ms.assetid: 585b0a3a-f85b-4f92-81bb-9ca499bb8a89
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 17f72cf130c5ff0f2d6d03ca8c460aa98ea39111
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739547"
---
# <a name="create-an-extension-with-a-tool-window"></a>Araç penceresi ile uzantı oluşturma

Bu yordamda, araç penceresi olan bir uzantı oluşturmak için VSIX proje şablonu ve **Özel Araç Penceresi** öğesi şablonu nasıl kullanılacağını öğrenirsiniz.

## <a name="prerequisites"></a>Ön koşullar

 Visual Studio 2015'ten itibaren Visual Studio SDK'yı indirme merkezinden yüklemezsiniz. Visual Studio kurulumunda isteğe bağlı bir özellik olarak yer almaktadır. VS SDK'yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için Visual [Studio SDK'yı yükleyin.](../extensibility/installing-the-visual-studio-sdk.md)

### <a name="create-a-tool-window"></a>Araç penceresi oluşturma

1. **FirstWindow**adında bir VSIX projesi oluşturun. "vsix" aramasını yaparak **VSIX** proje şablonunu Yeni Proje iletişim kutusunda bulabilirsiniz.

2. Proje açıldığında, **MyWindow**adlı bir araç penceresi öğesi şablonu ekleyin. Çözüm **Gezgini'nde**proje düğümüne sağ tıklayın ve**Yeni Öğe** **Ekle'yi** > seçin. Yeni **Öğe Ekle** iletişim kutusunda Visual **C#** > **Genişletilebilirlik'e** gidin ve Özel **Araç Penceresi'ni**seçin. Pencerenin altındaki **Ad** alanında, araç penceresi dosya adını *MyWindow.cs.*

3. Projeyi oluşturun ve hata ayıklamaya başlayın.

   Visual Studio'nun deneysel örneği ortaya çıkar. Deneysel örnek hakkında daha fazla bilgi için, [bkz.](../extensibility/the-experimental-instance.md)

4. Deneme örneğinde,**Diğer Windows'u** **Görüntüle'ye** > gidin.

   **MyWindow**için bir menü öğesi görmeniz gerekir. Tıklayın.

   **MyWindow** başlığı nı taşıyan bir araç penceresi ve **"Beni Tıklatın"** yazan bir düğme görmelisiniz.
