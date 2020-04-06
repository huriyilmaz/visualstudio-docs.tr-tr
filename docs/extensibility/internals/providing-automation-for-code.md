---
title: Kod için Otomasyon Sağlanması | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- CodeModel object
ms.assetid: 21cb3e63-f25c-404b-bc1d-a32ad0fdd4d5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bd13b7db2065069ff1540dbfc921570c2b230b8a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705986"
---
# <a name="providing-automation-for-code"></a>Kod için Otomasyon Sağlama
Kodunuz için bir otomasyon modeli oluşturmak gerekmez. Çevre SDK bunu yapmak için bir örnek sağlamaz. Kod modellerihakkında bilgi edinmek <xref:EnvDTE.CodeModel> için nesneye bakın.

 Bir kod modeli uygulamak için, iç veri yapınız tarafından belirlenen tüm arabirimleri uygulamanız gerekir. Nesneler `IDispatch` sınıftan türetilmelidir.

 Uzattığınız <xref:EnvDTE.CodeModel> ve <xref:EnvDTE.FileCodeModel>, <xref:EnvDTE.Project> nesneden edindiğiniz nesneler aşağıdaki gibi görünür:

- <xref:EnvDTE.Project.CodeModel%2A>

- <xref:EnvDTE.ProjectItem.FileCodeModel%2A>

 Sizden `Project` ve <xref:EnvDTE.ProjectItem> nesnelerden `CodeModel` döndürettiğiniz nesnedeki yalnızca `FileCodeModel` arabirimi veya arabirimi uygulamayı seçebilirsiniz. Proje sisteminize uygun olan bu arabirimden herhangi bir işlevsellik sağlayın.

 Standart `CodeModel` ve `FileCodeModel` arabirimlerden kullanılamayan yöntemler veya özellikler gibi özellikler eklemek istiyorsanız, standarttan devralan kendi arabiriminizi oluşturun. Son kullanıcıların onu aramayı bilmesi için proje sisteminizle belgelediğinden emin olun. Standart arabirimi döndürür, ancak `QueryInterface` kullanıcı varsa yöntemi veya kabirimi arabiriminize arayabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Otomasyon Modeline Genel Bakış](../../extensibility/internals/automation-model-overview.md)
