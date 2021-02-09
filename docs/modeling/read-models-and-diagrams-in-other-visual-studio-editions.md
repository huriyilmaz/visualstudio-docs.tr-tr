---
title: Diğer Visual Studio sürümlerindeki modelleri ve diyagramları okuma
description: Visual Studio 'da modelleri ve diyagramları okuma ve model oluşturmayı desteklemeyen bir Visual Studio sürümü kullanılırken salt okuma davranışı hakkında bilgi edinin.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- models, versions of Visual Studio
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a8049471e9e172496381df016c6155410f3bc244
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882940"
---
# <a name="read-models-and-diagrams-in-other-visual-studio-editions"></a>Diğer Visual Studio sürümlerindeki modelleri ve diyagramları okuma

Model oluşturmayı desteklemeyen bir Visual Studio sürümünde model açtığınızda, model salt okuma modunda açılır. Bu modda, diyagramların yerleşimini değiştirebilirsiniz, ancak modeli değiştiremezsiniz.

Hangi Visual Studio sürümünün model oluşturmayı desteklediğini görmek için bkz. [mimari ve modelleme araçları Için sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="obtaining-access-to-a-model-and-diagrams"></a>Model ve diyagramlara erişim sağlama

Bir bağımlılık diyagramını okumak için öncelikle Visual Studio 'Yu kullanarak modelleme projesini açın ve sonra diyagramı içinde açın.

Bu nedenle, bir bağımlılık diyagramını okumak istiyorsanız, oluşturulduğu modelleme projesine de erişiminizin olması gerekir. Bunu, projeye kaynak denetiminden erişerek ya da proje dosyalarının bir kopyasını alarak yapabilirsiniz.

> [!NOTE]
> Bu, koddan oluşturulan kod haritaları ve .NET sınıf diyagramları için geçerlidir. Bu diyagramlar, modelleme projesinden bağımsız olarak görüntülenebilir.

Bir bağımlılık diyagramını okumak için, ihtiyacınız olan minimum dosya kümesi aşağıdaki gibidir:

- Okumak istediğiniz diyagram için iki Diyagram dosyası; örneğin, **MyDiagram. classdiagram ve MyDiagram. classdiagram. Layout**.

    > [!NOTE]
    > Bağımlılık diyagramlarında, _MyDiagram_**. layerdiagram. suppressions** adlı dosyaya da sahip olmanız gerekir.

- Modelleme proje dosyası (**MyModel. modelproj**)

- Kök model dosyası (**Modeldefinition\mymodel.exe**)

- Diyagramda başvurulan herhangi bir paket için paket dosyaları (**Modeldefinition\mypackage.exe**)

## <a name="changes-that-you-can-make-in-read-only-mode"></a>Read-Only modunda yapabileceğiniz değişiklikler

Model oluşturmayı desteklemeyen bir Visual Studio sürümünde model ve diyagramlarını açarsanız modeli değiştiremezsiniz. Diğer bir deyişle, diyagramlarda veya model Gezgininde görüntülenen öğeleri ve ilişkileri değiştiremezsiniz. Ancak, diyagramların düzeninde bazı değişiklikler yapabilirsiniz:

- Diyagramdaki şekilleri ve bağlayıcıları yeniden düzenleyin.

- Şekilleri Genişlet ve daralt.

Bu değişiklikleri kaydedebilirsiniz. Değişikliklerinizi diğer kullanıcılara görünür yapmak istiyorsanız, en azından güncelleştirilmiş **. Layout** dosyalarını göndermeniz gerekir.

## <a name="see-also"></a>Ayrıca bkz.

- [Bağımlılık Diyagramları: Başvuru](../modeling/layer-diagrams-reference.md)
- [Uygulamanız için model oluşturma](../modeling/create-models-for-your-app.md)
