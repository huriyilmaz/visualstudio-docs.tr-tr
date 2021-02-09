---
title: Python kodunun performans ölçümü
description: Cpyıthon tabanlı yorumlayıcıları kullanırken Python kodunun performansını denetlemek için Visual Studio Profiler 'ı kullanın.
ms.date: 11/12/2018
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: d860acad409f553a90186e6898077e7bfd81dd90
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99918878"
---
# <a name="profile-python-code"></a>Profil Python kodu

Cpyıthon tabanlı yorumlayıcıları kullanırken bir Python uygulaması profili oluşturabilirsiniz. (Bkz. [Özellikler matrisi-](overview-of-python-tools-for-visual-studio.md#matrix-profiling) Visual Studio 'nun farklı sürümleri için bu özelliğin kullanılabilirliği için profil oluşturma.)

## <a name="profiling-for-cpython-based-interpreters"></a>Cpyıthon tabanlı yorumlayıcılar için profil oluşturma

Profil oluşturma   >  , bir yapılandırma iletişim kutusu açılan hata ayıklama **Python profil oluşturma** menü komutuyla başlatılır:

![Profil oluşturma yapılandırması iletişim kutusu](media/profiling-start.png)

**Tamam**' ı seçtiğinizde, profil oluşturucu çalışır ve uygulamada saatin nasıl harcandığını keşfedebileceğiniz bir performans raporu açar:

![Profil oluşturma performans raporu](media/profiling-results.png)

> [!Note]
> Bir Python uygulamasını profil oluştururken Visual Studio, işlemin ömrü boyunca verileri toplar. Mevcut olduğunda, profil oluşturmayı duraklatmak mümkün değildir. Gelecekteki özelliklerde geri bildirimlerinizi duymak istiyoruz. Bu sayfanın altındaki **ürün geri bildirim** düğmesini kullanın.

## <a name="profiling-for-ironpython"></a>IronPython için profil oluşturma

IronPython bir Cponthon tabanlı yorumlayıcı olmadığından, yukarıdaki profil oluşturma özelliği çalışmaz.

Bunun yerine, başlangıç komut dosyanızı başlatmak için uygun bağımsız değişkenleri kullanarak doğrudan hedef uygulama olarak *ipy.exe* başlatarak Visual Studio .net Profiler 'ı kullanın. `-X:Debug`Tüm Python kodunuzun hata ayıklamakta ve profili oluşturulabilir olduğundan emin olmak için komut satırına ekleyin. Bu bağımsız değişken, hem IronPython çalışma zamanında hem de kodunuzda harcanan süre de dahil olmak üzere bir performans raporu oluşturur. Kodunuz karıştırılmış adlar kullanılarak tanımlanır.

Alternatif olarak, IronPython kendi yerleşik profillerinden bazılarına sahiptir ancak şu anda onun için uygun Görselleştirici yoktur. Kullanılabilecek özellikler için [bir IronPython Profiler](/archive/blogs/curth/an-ironpython-profiler) 'a (MSDN blogları) bakın.