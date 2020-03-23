---
title: Python kodunun performansını ölçme
description: CPython tabanlı yorumlayıcıları kullanırken Python kodunun performansını denetlemek için Visual Studio profiloluşturucusunu kullanın.
ms.date: 11/12/2018
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: e31286a9b0ea3852ad1fe788d4ff6c4c66e7e4f0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62784291"
---
# <a name="profile-python-code"></a>Profil Python kodu

CPython tabanlı yorumlayıcıları kullanırken Python uygulamasının profilini oluşturabilirsiniz. (Bkz. [Özellikler matrisi -](overview-of-python-tools-for-visual-studio.md#matrix-profiling) Visual Studio'nun farklı sürümleri için bu özelliğin kullanılabilirliği için profil oluşturma.)

## <a name="profiling-for-cpython-based-interpreters"></a>CPython tabanlı tercümanlar için profil oluşturma

Profil oluşturma, yapılandırma iletişim kutusunu açan Python**Profil Oluşturma** menüsünü **çözümle** > komutu yla başlatılır:

![Profil oluşturma yapılandırma iletişim kutusu](media/profiling-start.png)

**Tamam'ı**seçtiğinizde, profil oluşturucu çalışır ve uygulamada zamanın nasıl harcandırdığını keşfedebileceğiniz bir performans raporu açar:

![Performans raporu profil oluşturma](media/profiling-results.png)

> [!Note]
> Şu anda, Visual Studio tam uygulama profilleme sadece bu düzeyde destekler, ama biz kesinlikle gelecekteki yetenekleri hakkında geribildirim duymak istiyorum. Bu sayfanın altındaki **Ürün geri bildirimi** düğmesini kullanın.

## <a name="profiling-for-ironpython"></a>IronPython için Profil Oluşturma

IronPython CPython tabanlı bir yorumlayıcı olmadığından, yukarıdaki profil oluşturma özelliği çalışmaz.

Bunun yerine, başlangıç komut dosyanızı başlatmak için uygun bağımsız değişkenleri kullanarak doğrudan hedef uygulama olarak *ipy.exe* başlatarak Visual Studio .NET profiloluşturucusunu kullanın. Python `-X:Debug` kodunun tümünün silinip profilinin silinip profilinin silinediğinden emin olmak için komut satırına ekleyin. Bu bağımsız değişken, hem IronPython çalışma zamanında hem de kodunuzda harcanan zamanı içeren bir performans raporu oluşturur. Kodunuz ezilmiş adlar kullanılarak tanımlanır.

Alternatif olarak, IronPython bazı kendi yerleşik profilleme var ama şu anda bunun için iyi bir görselleştirici var. Mevcut olanlar için [Bir IronPython Profiler](https://blogs.msdn.microsoft.com/curth/2009/03/30/an-ironpython-profiler/) (MSDN bloglar) bakın.
