---
title: Bağımlılık diyagramlarını genişletme
description: Bağımlılık diyagramları oluşturmak ve güncelleştirmek için kod yazmayı ve program kodunuzun yapısını veri akışındaki bağımlılık diyagramlarına karşı doğrulamayı Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams, creating extensions
- layer models
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c2ed8700cfb18aacf41464bfdfacaedac557bb00
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388912"
---
# <a name="extend-dependency-diagrams"></a>Bağımlılık diyagramlarını genişletme

Bağımlılık diyagramları oluşturmak ve güncelleştirmek ve program kodunuzun yapısını veri akışındaki bağımlılık diyagramlarına karşı doğrulamak için kod Visual Studio. Diyagramların kısayol (bağlam) menüsünde görünen komutlar ekleyebilir, sürükle ve bırak hareketlerini özelleştirilebilir ve metin şablonlarından katman modeline erişebilirsiniz. Bu uzantıları Visual Studio Integration Extension (VSIX) olarak paket haline Visual Studio.

## <a name="requirements"></a>Gereksinimler

Katman uzantılarınızı geliştirmek istediğiniz bilgisayarda aşağıdakilerin yüklü olması gerekir:

- Visual Studio

- [Visual Studio SDK](../extensibility/visual-studio-sdk.md)

- Visual Studio için Modelleme SDK'sı

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

Katman uzantılarınızı çalıştırmak istediğiniz Visual Studio uygun bir sürümü yüklü olmalıdır. Bağımlılık diyagramlarını destekleyen Visual Studio sürümleri görmek için bkz. [Mimari ve modelleme araçları için sürüm desteği.](../modeling/analyze-and-model-your-architecture.md#VersionSupport)

## <a name="see-also"></a>Ayrıca bkz.

- [Bağımlılık Diyagramları: Başvuru](../modeling/layer-diagrams-reference.md)
- [Bağımlılık Diyagramları: Yönergeler](../modeling/layer-diagrams-guidelines.md)
- [Kodunuz aracılığıyla bağımlılık diyagramları oluşturma](../modeling/create-layer-diagrams-from-your-code.md)
- [Bağımlılık diyagramları ile kod doğrulama](../modeling/validate-code-with-layer-diagrams.md)
