---
title: Görselleştirme ve SDK modelleme için desteklenen Visual Studio sürümleri
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, supported Visual Studio editions
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3be233ce8730879c2f0406ec9cc180685992c6bf
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544943"
---
# <a name="supported-visual-studio-editions-for-visualization--modeling-sdk"></a>Görselleştirme ve Modelleme SDK’sı için Desteklenen Visual Studio Sürümleri

Aşağıda, [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] yazma ve dağıtım ortamlarında ile desteklenen Visual Studio sürümleri listelenmiştir. Bu sürümler hakkında daha fazla bilgi için Microsoft Visual Studio [Geliştirici Merkezi](https://visualstudio.microsoft.com/)' ne bakın.

## <a name="authoring-edition"></a>Yazma sürümü

Bir DSL tanımlamak için aşağıdaki bileşenleri yüklemiş olmanız gerekir:

|Ürün|İndirme bağlantısı|
|-|-|
|Visual Studio|[http://go.microsoft.com/fwlink/?LinkId=185579](https://visualstudio.microsoft.com/)|
|Visual Studio SDK|[http://go.microsoft.com/fwlink/?LinkId=185580](/azure/devops/integrate/index?view=azure-devops&viewFallbackFrom=vsts)|
|Visual Studio görselleştirme ve modelleme SDK|[http://go.microsoft.com/fwlink/?LinkID=186128](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db)|

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="deployment-editions"></a>Dağıtım sürümleri

[!INCLUDE[dsl](../modeling/includes/dsl_md.md)], oluşturduğunuz alana özgü dillerin dağıtımı için aşağıdaki konfigürasyonları destekler:

- Visual Studio Enterprise

- Visual Studio Professional

- Visual Studio Kabuğu (tümleşik mod) yeniden dağıtılabilir paket yeniden dağıtılabilir paketi

- Visual Studio Kabuğu (yalıtılmış mod) yeniden dağıtılabilir paket yeniden dağıtılabilir paketi

> [!NOTE]
> Bir DSL 'yi bir kabuk ürününde çalışabilecek hale getirmek için, uzantı bildiriminde **desteklenen vs Edition** alanını ayarlamanız gerekir. Daha fazla bilgi için bkz. [etki alanına özgü dil çözümlerini dağıtma](msi-and-vsix-deployment-of-a-dsl.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Alana Özgü Dil Araçları sözlüğü](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
