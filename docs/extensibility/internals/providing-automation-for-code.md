---
title: Kod için Otomasyon sağlama | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- CodeModel object
ms.assetid: 21cb3e63-f25c-404b-bc1d-a32ad0fdd4d5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 874446aa6bf2e40a120aac49e7d91fd3d861d1d4
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72724968"
---
# <a name="providing-automation-for-code"></a>Kod için Otomasyon Sağlama
Kodunuz için bir otomasyon modeli oluşturmak gerekli değildir. Ortam SDK 'Sı bu işlemi gerçekleştirmek için bir örnek sağlamaz. Kod modellerine ilişkin Öngörüler için <xref:EnvDTE.CodeModel> nesnesine bakın.

 Bir kod modeli uygulamak için, iç veri yapınız tarafından belirlenen arabirimleri uygulamanız gerekir. Nesneler `IDispatch` sınıfından türetilmelidir.

 @No__t_0 ve <xref:EnvDTE.FileCodeModel> genişletmediğiniz nesneler <xref:EnvDTE.Project> nesnesinden kullanılabilir ve aşağıdakiler gibi görünür:

- <xref:EnvDTE.Project.CodeModel%2A>

- <xref:EnvDTE.ProjectItem.FileCodeModel%2A>

 @No__t_2 ve <xref:EnvDTE.ProjectItem> nesnelerinden aldığınız nesnede yalnızca `CodeModel` veya `FileCodeModel` arabirimini uygulamayı seçebilirsiniz. Bu arabirimden proje sisteminiz için uygun olan tüm işlevleri sağlayın.

 Standart `CodeModel` ve `FileCodeModel` arabirimlerinden kullanılamayan Yöntemler veya özellikler gibi özellikler eklemek istiyorsanız, standart 'dan devralan kendi arabirimini oluşturun. Son kullanıcıların bunu arayacağı bilmesini sağlamak için, bunu proje sisteminizle birlikte belgelediğinizden emin olun. Standart arabirimini döndürürler ancak Kullanıcı, varsa `QueryInterface` yöntemini çağırabilir veya varsa arabiriminize dönüşebilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Otomasyon Modeline Genel Bakış](../../extensibility/internals/automation-model-overview.md)