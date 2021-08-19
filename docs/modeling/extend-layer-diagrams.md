---
title: Bağımlılık diyagramlarını genişletme
description: Bağımlılık diyagramları oluşturmak ve güncelleştirmek için nasıl kod yazabilir ve Visual Studio ' deki bağımlılık diyagramlarına karşı program kodunuzun yapısını nasıl doğrulayabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams, creating extensions
- layer models
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 4b51d2754ec3c48c9ca2f7a86640959221ff2a28
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122040352"
---
# <a name="extend-dependency-diagrams"></a>Bağımlılık diyagramlarını genişletme

Bağımlılık diyagramları oluşturup güncelleştirmek ve Visual Studio içindeki bağımlılık diyagramlarına karşı program kodunuzun yapısını doğrulamak için kod yazabilirsiniz. Diyagramların kısayol (bağlam) menüsünde görünen komutları ekleyebilirsiniz, sürükle ve bırak hareketlerini özelleştirebilir ve metin şablonlarından katman modeline erişebilirsiniz. bu uzantıları bir Visual Studio tümleştirme uzantısı 'na (vsıx) paketleyebilir ve diğer Visual Studio kullanıcılarına dağıtabilirsiniz.

## <a name="requirements"></a>Gereksinimler

Katman uzantılarınızı geliştirmek istediğiniz bilgisayarda aşağıdakilerin yüklü olması gerekir:

- Visual Studio

- [Visual Studio SDK](../extensibility/visual-studio-sdk.md)

- Visual Studio için SDK modelleme

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

katman uzantılarınızı çalıştırmak istediğiniz bilgisayarda uygun bir Visual Studio sürümünün yüklü olması gerekir. hangi Visual Studio sürümlerinin bağımlılık diyagramlarını desteklediğini görmek için bkz. [mimari ve modelleme araçları için sürüm desteği](../modeling/analyze-and-model-your-architecture.md#VersionSupport).

## <a name="see-also"></a>Ayrıca bkz.

- [Bağımlılık Diyagramları: Başvuru](../modeling/layer-diagrams-reference.md)
- [Bağımlılık Diyagramları: Yönergeler](../modeling/layer-diagrams-guidelines.md)
- [Kodunuz aracılığıyla bağımlılık diyagramları oluşturma](../modeling/create-layer-diagrams-from-your-code.md)
- [Bağımlılık diyagramları ile kod doğrulama](../modeling/validate-code-with-layer-diagrams.md)
