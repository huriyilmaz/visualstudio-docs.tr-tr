---
title: Proje Derlemek için Birden Çok İşlemci | Microsoft Docs
description: Kullanılabilir her MSBuild ayrı bir derleme işlemi oluşturarak birden çok işlemciye veya çekirdeke sahip sistemlerden nasıl faydalanıyor?
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
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 814db4514454659780021c17e873a8e2363cb54f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122142448"
---
# <a name="use-multiple-processors-to-build-projects"></a>Proje derlemek için birden çok işlemci kullanma

MSBuild, birden çok işlemciye veya birden çok çekirdekli işlemciye sahip sistemlerden faydalanma. Kullanılabilir her işlemci için ayrı bir derleme işlemi oluşturulur. Örneğin, sistemde dört işlemci varsa dört derleme işlemi oluşturulur. MSBuild bu derlemeleri aynı anda işleyene kadar devam ediyor ve bu nedenle genel derleme süresi azaltıldı. Ancak paralel bina, derleme işlemlerinin nasıl oluştuğunda bazı değişikliklere neden olur. Bu konu başlığında bu değişiklikler ele ele ve açıklamalanmıştır.

## <a name="project-to-project-references"></a>Project proje başvuruları

 Proje Microsoft Build Engine için paralel derlemeler kullanırken projeden projeye (P2P) başvuruyla karşılaştığında, yalnızca bir kez başvuru derlemesini sağlar. İki proje aynı P2P başvurusuna sahipse, başvuru her proje için yeniden oluşturulmuş değildir. Bunun yerine, derleme altyapısı buna bağımlı her iki proje için de aynı P2P başvurularını döndürür. Oturumda aynı hedef için gelecekteki isteklere aynı P2P başvurusu sağlanır.

## <a name="cycle-detection"></a>Döngü algılama

 Döngü algılama işlevleri, MSBuild 2.0'da olduğu gibi işlev gösterir, ancak MSBuild farklı bir zamanda veya derlemede döngü algılamayı bildirebilirsiniz.

## <a name="errors-and-exceptions-during-parallel-builds"></a>Paralel derlemeler sırasında hatalar ve özel durumlar

 Paralel derlemelerde hatalar ve özel durumlar, paralel olmayan bir derlemede olduğu gibi farklı zamanlarda oluşabilir ve bir proje oluşturmazsa diğer proje derlemeleri devam eder. MSBuild, başarısız olanla paralel olarak derlemesi yapılan herhangi bir proje derlemesini durdurmaz. Diğer projeler başarılı veya başarısız olana kadar derlemeye devam eder. Ancak, <xref:Microsoft.Build.Framework.IBuildEngine.ContinueOnError%2A> etkinleştirildiyse, hata oluştuğunda bile hiçbir derleme durmaz.

## <a name="c-project-vcxproj-and-solution-sln-files"></a>C++ projesi (.vcxproj) ve çözüm (.sln) dosyaları

 Hem C++ projeleri (*.vcxproj*) hem de çözüm (*.sln*) dosyaları MSBuild [geçirebilirsiniz.](../msbuild/msbuild-task.md) C++ projeleri için VCWrapperProject çağrılır ve ardından iç MSBuild projesi oluşturulur. C++ çözümleri için bir SolutionWrapperProject oluşturulur ve ardından iç MSBuild projesi oluşturulur. Her iki durumda da, sonuçta elde edilen proje diğer tüm projelerde olduğu MSBuild kabul edilir.

## <a name="multi-process-execution"></a>Çok işlemli yürütme

 Derlemeyle ilgili etkinliklerin neredeyse hepsi, yol ile ilgili hataları önlemek için geçerli dizinin derleme işlemi boyunca sabit kalmasını gerektirir. Bu nedenle, birden çok dizinin oluşturulmalarına neden MSBuild projelerde farklı iş parçacıkları üzerinde çalıştıramaz.

 Bu sorundan kaçınmak ama yine de çok işlemcili derlemeleri etkinleştirmek MSBuild "işlem yalıtımı" kullanır. İşlem yalıtımı kullanarak MSBuild, sistem üzerinde kullanılabilir işlemci sayısına eşit `n` olan en fazla işlem `n` oluşturabilirsiniz. Örneğin, MSBuild işlemciye sahip bir sistemde çözüm derlemesi varsa, yalnızca iki derleme işlemi oluşturulur. Bu işlemler, çözümde tüm projeleri derlemek için yeniden kullanılır.

## <a name="see-also"></a>Ayrıca bkz.

- [Birden çok proje paralel olarak derleme](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)
- [Görevler](../msbuild/msbuild-tasks.md)
