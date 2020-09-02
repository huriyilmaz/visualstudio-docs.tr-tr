---
title: Projeleri derlemek için birden çok Işlemci kullanma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- multiple processors
- MSBuild, multiple processor systems
ms.assetid: 49fa36c9-8e14-44f5-8a2b-34146cf6807b
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3a590d3dc3053c5b857917dc358e32a2c7d5247c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68192861"
---
# <a name="using-multiple-processors-to-build-projects"></a>Projeleri Derlemek için Birden Çok İşlemci Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

MSBuild, birden çok işlemciyi veya birden çok çekirdekli işlemciyi olan sistemlerden yararlanabilir. Kullanılabilir her işlemci için ayrı bir yapı işlemi oluşturulur. Örneğin, sistemde dört işlemci varsa dört yapı işlemi oluşturulur. [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] Bu yapıları aynı anda işleyebilir ve bu nedenle genel derleme süresi azaltılır. Ancak paralel oluşturma, derleme işlemlerinin oluşma biçiminde bazı değişiklikler sunar. Bu konuda bu değişiklikler ele alınmaktadır.  
  
## <a name="project-to-project-references"></a>Projeden Projeye Başvurular  
 Bir proje [!INCLUDE[vstecmsbuildengine](../includes/vstecmsbuildengine-md.md)] oluşturmak için paralel derlemeler kullanırken bir projeden projeye (P2P) başvurusuyla karşılaştığında, başvuruyu yalnızca bir kez oluşturur. İki proje aynı P2P başvurusuna sahip ise, başvuru her bir proje için yeniden derlenmez. Bunun yerine, derleme altyapısı, kendisine bağımlı olan projelere aynı P2P başvurusunu döndürür. Aynı hedefe yönelik oturumdaki gelecekteki isteklere aynı P2P başvurusu sunulmaktadır.  
  
## <a name="cycle-detection"></a>Döngü Algılama  
 Döngüsellik algılama işlevi 2,0 ' de olduğu gibi çalışır [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] , ancak artık [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] döngüyü farklı bir zamanda veya yapıda tespit edebilir.  
  
## <a name="errors-and-exceptions-during-parallel-builds"></a>Paralel Yapılar Sırasında Hatalar ve Özel Durumlar  
 Paralel derlemelerde, hatalar ve özel durumlar, paralel olmayan bir derlemede olduklarından farklı zamanlarda ve bir proje oluşturmadığı zaman, diğer proje de devam eder. [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] , başarısız olan ile paralel olarak oluşturmakta olan herhangi bir proje derlemesini durdurmayacak. Diğer projeler, başarılı veya başarısız olana kadar derlenmeye devam eder. Ancak, <xref:Microsoft.Build.Framework.IBuildEngine.ContinueOnError%2A> etkinleştirilirse bir hata oluşsa bile hiçbir derleme durdurulur.  
  
## <a name="visual-c-project-vcproj-and-solution-sln-files"></a>Visual C++ Projesi (.vcproj) ve Çözüm (.sln) Dosyaları  
 Hem [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] projeler (. vcproj) hem de çözüm (. sln) dosyaları [MSBuild görevine](../msbuild/msbuild-task.md)geçirilebilir. [!INCLUDE[vcprvc](../includes/vcprvc-md.md)]Projeler Için VCWrapperProject çağrılır ve sonra iç [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] Proje oluşturulur. [!INCLUDE[vcprvc](../includes/vcprvc-md.md)]Çözümler için bir SolutionWrapperProject oluşturulur ve ardından iç [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] Proje oluşturulur. Her iki durumda da, sonuçta elde edilen proje diğer tüm projeler ile aynı şekilde değerlendirilir [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] .  
  
## <a name="multi-process-execution"></a>Birden Çok İşlem Yürütme  
 Neredeyse tüm derleme ile ilgili etkinlikler, yol ile ilgili hataları engellemek için derleme işlemi boyunca geçerli dizinin sabit kalmasını gerektirir. Bu nedenle, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] birden çok dizinlerin oluşturulmasına neden olacağından, projeleri içindeki farklı iş parçacıklarında çalıştırılamaz.  
  
 Bu sorundan kaçınmak ve çok işlemcili yapıları etkinleştirmek için, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] "işlem yalıtımı" kullanır. İşlem yalıtımını kullanarak, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] `n` `n` sistemdeki kullanılabilir işlemci sayısına eşit olan en fazla işlem oluşturulabilir. Örneğin, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] iki işlemcili bir sistemde bir çözüm oluşturduğunda, yalnızca iki derleme işlemi oluşturulur. Bu süreçler Çözümdeki tüm projeleri oluşturmak için yeniden kullanılır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Paralel olarak birden çok proje oluşturma](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)   
 [Görevler](../msbuild/msbuild-tasks.md)
