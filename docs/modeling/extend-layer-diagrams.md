---
title: Bağımlılık diyagramlarını genişletme
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
ms.openlocfilehash: 305c562c7600dc6955ce0307db92f4e257fc1c21
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302947"
---
# <a name="extend-dependency-diagrams"></a>Bağımlılık diyagramlarını genişletme

Bağımlılık diyagramları oluşturmak ve güncelleştirmek ve Program kodunuzu Visual Studio'daki bağımlılık diyagramlarına karşı doğrulamak için kod yazabilirsiniz. Diyagramların kısayol (bağlam) menüsünde görünen komutlar ekleyebilir, sürükle ve bırak hareketlerini özelleştirebilir ve metin şablonlarından katman modeline erişebilirsiniz. Bu uzantıları Visual Studio Tümleştirme Uzantısı 'na (VSIX) paketleyebilir ve diğer Visual Studio kullanıcılarına dağıtabilirsiniz.

## <a name="requirements"></a>Gereksinimler

Katman uzantılarınızı geliştirmek istediğiniz bilgisayarda aşağıdakileri yüklemelisiniz:

- Visual Studio

- [Visual Studio SDK](../extensibility/visual-studio-sdk.md)

- Visual Studio için SDK modelleme

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

Katman uzantılarınızı çalıştırmak istediğiniz bilgisayarda Visual Studio'nun uygun bir sürümü yüklü olmalıdır. Visual Studio'nun hangi sürümlerinin bağımlılık diyagramlarını desteklediğini görmek [için mimari ve modelleme araçları için Edition desteğine](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [Bağımlılık Diyagramları: Başvuru](../modeling/layer-diagrams-reference.md)
- [Bağımlılık Diyagramları: Yönergeler](../modeling/layer-diagrams-guidelines.md)
- [Kodunuz aracılığıyla bağımlılık diyagramları oluşturma](../modeling/create-layer-diagrams-from-your-code.md)
- [Bağımlılık diyagramları ile kod doğrulama](../modeling/validate-code-with-layer-diagrams.md)
