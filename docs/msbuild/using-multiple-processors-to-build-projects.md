---
title: Projeleri derlemek için birden çok Işlemci kullanma | Microsoft Docs
description: MSBuild 'in, kullanılabilir her işlemci için ayrı bir yapı işlemi oluşturarak birden çok işlemciyi veya çekirdeği olan sistemlerden nasıl yararlanaldığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- multiple processors
- MSBuild, multiple processor systems
ms.assetid: 49fa36c9-8e14-44f5-8a2b-34146cf6807b
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c1560b40fe94af8dae5223981dd8e0c790320085
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99946377"
---
# <a name="use-multiple-processors-to-build-projects"></a>Projeleri derlemek için birden çok işlemci kullanma

MSBuild, birden çok işlemciyi veya birden çok çekirdekli işlemciyi olan sistemlerden yararlanabilir. Kullanılabilir her işlemci için ayrı bir yapı işlemi oluşturulur. Örneğin, sistemde dört işlemci varsa dört yapı işlemi oluşturulur. MSBuild bu yapıları aynı anda işleyebilir ve bu nedenle genel derleme süresi azaltılır. Ancak paralel oluşturma, derleme işlemlerinin oluşma biçiminde bazı değişiklikler sunar. Bu konuda bu değişiklikler ele alınmaktadır.

## <a name="project-to-project-references"></a>Projeden projeye başvurular

 Microsoft Build Engine bir proje oluşturmak için paralel derlemeler kullanırken bir projeden projeye (P2P) başvurusuyla karşılaştığında, başvuruyu yalnızca bir kez oluşturur. İki proje aynı P2P başvurusuna sahip ise, başvuru her bir proje için yeniden derlenmez. Bunun yerine, derleme altyapısı, kendisine bağımlı olan projelere aynı P2P başvurusunu döndürür. Aynı hedefe yönelik oturumdaki gelecekteki isteklere aynı P2P başvurusu sunulmaktadır.

## <a name="cycle-detection"></a>Döngüyü algılama

 Geçiş algılaması, MSBuild 2,0 ' de olduğu gibi çalışır, ancak artık MSBuild, döngüdeki farklı bir zamanda veya derlemede algılanabilmesi için.

## <a name="errors-and-exceptions-during-parallel-builds"></a>Paralel derlemeler sırasında hatalar ve özel durumlar

 Paralel derlemelerde, hatalar ve özel durumlar, paralel olmayan bir derlemede olduklarından farklı zamanlarda ve bir proje oluşturmadığı zaman, diğer proje de devam eder. MSBuild, başarısız olan ile paralel olarak oluşturmakta olan herhangi bir proje derlemesini durdurmayacak. Diğer projeler, başarılı veya başarısız olana kadar derlenmeye devam eder. Ancak, <xref:Microsoft.Build.Framework.IBuildEngine.ContinueOnError%2A> etkinleştirilirse bir hata oluşsa bile hiçbir derleme durdurulur.

## <a name="c-project-vcxproj-and-solution-sln-files"></a>C++ projesi (. vcxproj) ve çözüm (. sln) dosyaları

 Hem C++ projeleri (*. vcxproj*) hem de çözüm (*. sln*) dosyaları [MSBuild görevine](../msbuild/msbuild-task.md)geçirilebilir. C++ projeleri için VCWrapperProject çağrılır ve sonra iç MSBuild projesi oluşturulur. C++ çözümleri için bir SolutionWrapperProject oluşturulur ve ardından iç MSBuild projesi oluşturulur. Her iki durumda da, sonuçta elde edilen proje diğer MSBuild projesiyle aynı şekilde değerlendirilir.

## <a name="multi-process-execution"></a>Çok işlem yürütme

 Neredeyse tüm derleme ile ilgili etkinlikler, yol ile ilgili hataları engellemek için derleme işlemi boyunca geçerli dizinin sabit kalmasını gerektirir. Bu nedenle, birden çok dizinlerin oluşturulmasına neden olacağından, projeler MSBuild 'te farklı iş parçacıkları üzerinde çalıştırılamaz.

 Bu sorundan kaçınmak ve çok işlemcili yapıları etkinleştirmek için MSBuild, "işlem yalıtımı" kullanır. MSBuild, işlem yalıtımı kullanarak, `n` `n` sistemdeki kullanılabilir işlemci sayısına eşit olan en fazla işlem oluşturabilir. Örneğin, MSBuild iki işlemcili bir sistemde bir çözüm oluşturduğunda, yalnızca iki derleme işlemi oluşturulur. Bu süreçler Çözümdeki tüm projeleri oluşturmak için yeniden kullanılır.

## <a name="see-also"></a>Ayrıca bkz.

- [Paralel olarak birden çok proje oluşturun](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)
- [Görevler](../msbuild/msbuild-tasks.md)
