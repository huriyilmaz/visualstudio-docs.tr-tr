---
title: VS kabuğu dağıtımı | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: be8f2ffe-a322-4ac0-9c9e-873bd28e5d5e
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a42ec6a762655589bfd589ae9dc0354e3a7d1cb5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659311"
---
# <a name="vs-shell-deployment"></a>VS Shell dağıtımı
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Yalıtılmış bir kabuk, etki alanına özgü diliniz ve bu çözümün görünmesi için hangi Visual Studio işlevselliğini kullanmanız gerektiğini belirlemenizi sağlar. Visual Studio yalıtılmış Kabuğu hakkında daha fazla bilgi için bkz. [yalıtılmış Kabuğu özelleştirme](../extensibility/customizing-the-isolated-shell.md). Yalıtılmış Kabuğu özelleştirmek için yalıtılmış Kabuğu özelleştirme hakkında daha fazla bilgi [edinebilirsiniz.](https://msdn.microsoft.com/d75463cd-1155-42e4-8b7a-046ed6becbbf)

### <a name="to-set-a-visual-studio-shell-as-the-deployment-target"></a>Bir Visual Studio kabuğunu dağıtım hedefi olarak ayarlamak için

1. **DslPackage** projesinde **Source.Extension.tt**öğesini açın.

2. @No__t_0 Ekle altında:

    ```
    <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>
    ```

     *MyIsolatedShell* öğesini yalıtılmış Kabuk paketinizin adıyla değiştirin.
