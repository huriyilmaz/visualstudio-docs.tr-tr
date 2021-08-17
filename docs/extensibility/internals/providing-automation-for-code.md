---
title: Kod Çözümleri için Otomasyon | Microsoft Docs
description: İç veri yapınız tarafından belirlenen arabirimlerin uygulanmasını gerektiren bir kod modeli uygulama hakkında bilgi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- CodeModel object
ms.assetid: 21cb3e63-f25c-404b-bc1d-a32ad0fdd4d5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 705fa036bdb0d76d02e9d4fcd540c3f3450c4f06
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122028897"
---
# <a name="providing-automation-for-code"></a>Kod için Otomasyon Sağlama
Kodunuz için otomasyon modeli oluşturmak gerekli değildir. Ortam SDK'sı bunu yapmak için bir örnek sağlamaz. Kod modelleri hakkında içgörüler için nesnesine <xref:EnvDTE.CodeModel> bakın.

 Bir kod modeli uygulamak için, iç veri yapınız tarafından belirlenen tüm arabirimleri uygulamanız gerekir. Nesneleri sınıfından `IDispatch` türetilen gerekir.

 ve gibi genişleten <xref:EnvDTE.CodeModel> nesneler <xref:EnvDTE.FileCodeModel> nesnesinden <xref:EnvDTE.Project> kullanılabilir ve aşağıdaki gibi olur:

- <xref:EnvDTE.Project.CodeModel%2A>

- <xref:EnvDTE.ProjectItem.FileCodeModel%2A>

 Ve nesnelerinden geri dönüş nesnesinde yalnızca veya `CodeModel` `FileCodeModel` arabirimini uygulamaya karar `Project` <xref:EnvDTE.ProjectItem> veebilirsiniz. Bu arabirimden proje sisteminiz için uygun olan tüm işlevleri sağlama.

 Standart ve arabirimlerden kullanılabilir olmayan yöntemler veya özellikler gibi özellikler eklemek için, standarttan devralınan kendi `CodeModel` `FileCodeModel` arabiriminizi oluşturun. Son kullanıcıların bunu nasıl bakacaklarını bilmek için bunu proje sisteminize belgeleyenin. Standart arabirimini geri dönersiniz, ancak kullanıcı yöntemini çağırarak veya mevcut olduğu `QueryInterface` biliniyorsa arabiriminize atabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [Otomasyon Modeline Genel Bakış](../../extensibility/internals/automation-model-overview.md)
