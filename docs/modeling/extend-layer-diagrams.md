---
title: Bağımlılık diyagramlarını genişletme
description: Bağımlılık diyagramları oluşturmak ve güncelleştirmek için nasıl kod yazabilir ve Visual Studio 'daki bağımlılık diyagramlarına karşı program kodunuzun yapısını nasıl doğrulayabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams, creating extensions
- layer models
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d78b7005875f0544354c845cd27d187bdbf40d6d
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/12/2020
ms.locfileid: "97361631"
---
# <a name="extend-dependency-diagrams"></a>Bağımlılık diyagramlarını genişletme

Bağımlılık diyagramları oluşturup güncelleştirmek ve Visual Studio 'daki bağımlılık diyagramlarına karşı program kodunuzun yapısını doğrulamak için kod yazabilirsiniz. Diyagramların kısayol (bağlam) menüsünde görünen komutları ekleyebilirsiniz, sürükle ve bırak hareketlerini özelleştirebilir ve metin şablonlarından katman modeline erişebilirsiniz. Bu uzantıları bir Visual Studio Tümleştirme Uzantısı 'na (VSıX) paketleyebilir ve diğer Visual Studio kullanıcılarına dağıtabilirsiniz.

## <a name="requirements"></a>Gereksinimler

Katman uzantılarınızı geliştirmek istediğiniz bilgisayarda aşağıdakilerin yüklü olması gerekir:

- Visual Studio

- [Visual Studio SDK](../extensibility/visual-studio-sdk.md)

- Visual Studio için modelleme SDK 'Sı

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

Katman uzantılarınızı çalıştırmak istediğiniz bilgisayarda, uygun bir Visual Studio sürümü yüklü olmalıdır. Hangi Visual Studio sürümlerini bağımlılık diyagramlarını desteklediğini görmek için bkz. [mimari ve modelleme araçları Için sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="see-also"></a>Ayrıca bkz.

- [Bağımlılık Diyagramları: Başvuru](../modeling/layer-diagrams-reference.md)
- [Bağımlılık Diyagramları: Yönergeler](../modeling/layer-diagrams-guidelines.md)
- [Kodunuz aracılığıyla bağımlılık diyagramları oluşturma](../modeling/create-layer-diagrams-from-your-code.md)
- [Bağımlılık diyagramları ile kod doğrulama](../modeling/validate-code-with-layer-diagrams.md)
