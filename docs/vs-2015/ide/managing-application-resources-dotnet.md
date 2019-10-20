---
title: Uygulama kaynaklarını yönetme (.NET) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- msvse_resedit.dlg.SetCustomTool
- msvse_settingsdesigner.err.formatvalue
- msvse_resedit.err.nameblank
- msvse_resedit.err.duplicatename
helpviewer_keywords:
- editors [Visual Studio], Resource Designer
- Resource Designer
- resources [Visual Studio], managing
- Resources page in Project Designer
- resources types, Resource Designer
- application resources [Visual Studio]
- Project Designer, Resources page
ms.assetid: f2582734-8ada-4baa-8a7c-e2ef943ddf7e
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: efe2b176db9f6f22f9e38775d5fc8acad87655ba
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651379"
---
# <a name="managing-application-resources-net"></a>Uygulama Kaynaklarını Yönetme (.NET)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kaynak dosyaları, bir uygulamanın parçası olan ancak derlenmediği, örneğin simge dosyaları veya ses dosyaları gibi dosyalardır. Bu dosyalar derleme sürecinin bir parçası olmadığından, ikili dosyalarınızı yeniden derlemek zorunda kalmadan bunları değiştirebilirsiniz. Uygulamanızı yerelleştirmek istiyorsanız, uygulamanızı yerelleştirmeniz durumunda değiştirilmesi gereken tüm dizelerin ve diğer kaynakların kaynak dosyalarını kullanmanız gerekir.

 .NET masaüstü uygulamalarındaki kaynaklar hakkında daha fazla bilgi için bkz. [masaüstü uygulamalarında kaynaklar](https://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890). C++ Masaüstü uygulamalarındaki kaynaklar hakkında daha fazla bilgi için bkz. [kaynak dosyalarıyla çalışma](https://msdn.microsoft.com/library/2699a539-b369-4b78-80f0-df03eb7b6780).

 Windows Mağazası uygulamaları, Masaüstü uygulamalarından farklı bir kaynak modeli kullanır. Windows Mağazası uygulamalarındaki kaynaklar hakkında daha fazla bilgi için, bkz. Windows Dev Center Web sitesinde [uygulama kaynaklarını tanımlama](https://msdn.microsoft.com/library/windows/apps/hh465228.aspx) .

## <a name="working-with-resources"></a>Kaynaklarla çalışma
 Yönetilen bir kod projesinde, proje özellikleri penceresini açın ( **Çözüm Gezgini** ' de proje düğümüne sağ tıklayın ve **Özellikler**' i seçin veya **Hızlı Başlat** penceresine **Proje özellikleri** yazın veya Alt + Enter yazın.  **Çözüm Gezgini** pencere). **Kaynaklar** sekmesini seçin. Projenizde bir tane yoksa bir. resx dosyası ekleyebilirsiniz, farklı türlerde kaynaklar ekleyip silebilir ve mevcut kaynakları değiştirebilirsiniz.

 C++ Projelerdeki kaynaklarla nasıl çalışabileceğinizi öğrenmek için bkz. [nasıl yapılır: kaynak oluşturma](https://msdn.microsoft.com/library/aad44914-9145-45a3-a7d8-9de89b366716).
