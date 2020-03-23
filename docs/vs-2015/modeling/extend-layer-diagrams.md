---
title: Katman diyagramlarını genişletme | Microsoft Dokümanlar
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- layer diagrams, creating extensions
- layer models
ms.assetid: 83fca301-b008-485a-87eb-218050e71451
caps.latest.revision: 41
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bfcec64f9401fdbf79e67bee5fe8430452632fbc
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302338"
---
# <a name="extend-layer-diagrams"></a>Katman diyagramlarını genişletme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Katman diyagramları oluşturmak ve güncelleştirmek ve Program kodunuzu Visual Studio'daki katman diyagramlarına göre doğrulamak için kod yazabilirsiniz. Diyagramların kısayol (bağlam) menüsünde görünen komutlar ekleyebilir, sürükle ve bırak hareketlerini özelleştirebilir ve metin şablonlarından katman modeline erişebilirsiniz. Bu uzantıları Visual Studio Tümleştirme Uzantısı 'na (VSIX) paketleyebilir ve diğer Visual Studio kullanıcılarına dağıtabilirsiniz.

 Katman diyagramları hakkında daha fazla bilgi için bkz:

- [Katman Diyagramları: Başvuru](../modeling/layer-diagrams-reference.md)

- [Katman Diyagramları: Yönergeler](../modeling/layer-diagrams-guidelines.md)

- [Kodunuz aracılığıyla katman diyagramları oluşturma](../modeling/create-layer-diagrams-from-your-code.md)

- [Katman diyagramları ile kod doğrulama](../modeling/validate-code-with-layer-diagrams.md)

## <a name="requirements"></a><a name="prereqs"></a>Gereksinim -leri
 Katman uzantılarınızı geliştirmek istediğiniz bilgisayarda aşağıdakileri yüklemelisiniz:

- Visual Studio

- [Visual Studio SDK](../extensibility/visual-studio-sdk.md)

- [Visual Studio 2015 için Modelleme SDK](https://www.microsoft.com/download/details.aspx?id=48148)

  Katman uzantılarınızı çalıştırmak istediğiniz bilgisayarda Visual Studio'nun uygun bir sürümü yüklü olmalıdır. Daha fazla bilgi için [bkz.](../modeling/deploy-a-layer-model-extension.md)

  Visual Studio'nun hangi sürümlerinin katman diyagramlarını desteklediğini görmek [için mimari ve modelleme araçları için Sürüm desteğine](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)bakın.

## <a name="in-this-section"></a>Bu Bölümde
 [Katman diyagramlarına komut ve hareket ekleme](../modeling/add-commands-and-gestures-to-layer-diagrams.md)

 [Katman diyagramlarına özel mimari doğrulaması ekleme](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)

 [Katman diyagramlarına özel özellikler ekleme](../modeling/add-custom-properties-to-layer-diagrams.md)

 [Program kodunda katman modellerini gezinme ve güncelleştirme](../modeling/navigate-and-update-layer-models-in-program-code.md)

 [Katman modeli uzantısı dağıtma](../modeling/deploy-a-layer-model-extension.md)

 [Katman diyagramları için genişletme sorunlarını giderme](../modeling/troubleshoot-extensions-for-layer-diagrams.md)

## <a name="see-also"></a>Ayrıca Bkz.
 [Tanımlama ve yükleme modelleme uzantısı](../modeling/define-and-install-a-modeling-extension.md) Katman Diyagramları: Başvuru Katmanı [Diyagramları:](../modeling/layer-diagrams-reference.md) [Yönergeler](../modeling/layer-diagrams-guidelines.md) [Kodunuzdan katman diyagramları oluşturma](../modeling/create-layer-diagrams-from-your-code.md) Katmanı [diyagramları katman diyagramları ile kod doğrula](../modeling/validate-code-with-layer-diagrams.md) bir [UML modelinden dosyaları oluşturma](../modeling/generate-files-from-a-uml-model.md) Visual Studio [API'sini kullanarak uml modelini açın](../modeling/open-a-uml-model-by-using-the-visual-studio-api.md)
