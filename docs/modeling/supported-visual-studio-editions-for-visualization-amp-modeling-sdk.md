---
title: görselleştirme ve modelleme SDK için desteklenen Visual Studio sürümleri
description: yazma ve dağıtım ortamlarında DSL araçlarıyla desteklenen Visual Studio sürümleri hakkında bilgi edinin.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, supported Visual Studio editions
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 661daaea4908a674e97c28f672ffc7f709429a8f
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126637409"
---
# <a name="supported-visual-studio-editions-for-visualization--modeling-sdk"></a>Görselleştirme ve Modelleme SDK’sı için Desteklenen Visual Studio Sürümleri

aşağıda, [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] yazma ve dağıtım ortamlarında ile desteklenen Visual Studio sürümlerinin listeleri verilmiştir. bu sürümler hakkında daha fazla bilgi için Microsoft Visual Studio [geliştirici merkezi](https://visualstudio.microsoft.com/)' ne bakın.

## <a name="authoring-edition"></a>Yazma sürümü

Bir DSL tanımlamak için aşağıdaki bileşenleri yüklemiş olmanız gerekir:

|Ürün|İndirme bağlantısı|
|-|-|
|Visual Studio|[http://go.microsoft.com/fwlink/?LinkId=185579](https://visualstudio.microsoft.com/)|
|Visual Studio SDK|[http://go.microsoft.com/fwlink/?LinkId=185580](/azure/devops/integrate/index?view=azure-devops&viewFallbackFrom=vsts&preserve-view=true)|
|Visual Studio Görselleştirme ve modelleme SDK 'Sı|[http://go.microsoft.com/fwlink/?LinkID=186128](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db)|

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="deployment-editions"></a>Dağıtım sürümleri

[!INCLUDE[dsl](../modeling/includes/dsl_md.md)] , oluşturduğunuz alana özgü dillerin dağıtımı için aşağıdaki konfigürasyonları destekler:

- Visual Studio Enterprise

- Visual Studio Professional

- Visual Studio Kabuk (tümleşik mod) yeniden dağıtılabilir paket yeniden dağıtılabilir paketi

- Visual Studio Kabuk (yalıtılmış mod) yeniden dağıtılabilir paket yeniden dağıtılabilir paketi

> [!NOTE]
> Bir DSL 'yi bir kabuk ürününde çalışabilecek hale getirmek için, uzantı bildiriminde **desteklenen vs Edition** alanını ayarlamanız gerekir. Daha fazla bilgi için bkz. [Domain-Specific dil çözümlerini dağıtma](msi-and-vsix-deployment-of-a-dsl.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Alana Özgü Dil Araçları sözlüğü](/previous-versions/bb126564(v=vs.100))