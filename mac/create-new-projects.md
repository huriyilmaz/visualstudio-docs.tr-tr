---
title: Yeni projeler ve çözümler oluşturma
description: bu makalede Mac için Visual Studio ' de projelerin ve çözümlerin nasıl oluşturulacağı açıklanmaktadır
author: heiligerdankgesang
ms.author: dominicn
ms.date: 11/06/2020
ms.assetid: 5880BB10-0A12-47E2-8A82-7A2D59C4D579
ms.openlocfilehash: c84fee5e4180caa59610fbcbcba85d3fc301341f7f77880f0a248f6bdde5fa06
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121266421"
---
# <a name="create-a-new-project"></a>Yeni bir Project oluştur

## <a name="opening-the-project-creation-dialog"></a>Project oluşturma iletişim kutusunu açma

Mac için Visual Studio yeni bir proje oluşturmanın birkaç yolu vardır. Mac için Visual Studio ilk kez açtığınızda başlangıç penceresi gösterilir. Buradan proje oluşturma ekranına kadar **Yeni** bir seçim yapabilirsiniz.

> [!TIP]
> Ayrıca, başlangıç penceresinde, son projeler ve çözümler için de açabilir ve arama yapabilirsiniz. Son projeleri de menü çubuğuna gidip **dosya > son çözümler** ' i seçerek açabilirsiniz.

![Yeni proje oluştur ile başlangıç penceresi](media/first-run-project.png)

Mac için Visual Studio yüklenmiş bir çözümle zaten açıksa, menü çubuğuna gidip **dosya > yeni çözüm**' i seçerek yeni bir çözüm oluşturabilirsiniz. Bu şekilde yeni bir çözüm oluşturulması, zaten yüklü olan çözümü kapatır.

## <a name="creating-a-new-project"></a>Yeni Project oluşturma

**yeni Project** iletişim kutusu varsayılan olarak son kullanılan şablonlarınızı *en son kullanılan* şablonları gösterir.

Son kullanılan bir şablonu kullanmak istemiyorsanız, iletişim kutusunun solundaki kategoriler arasından seçim yapabilirsiniz. Her kategori, aralarından seçim yapabileceğiniz çeşitli proje şablonları içerir. Proje türüne tıklanması, ekranın sağ tarafında bir açıklama görmenizi sağlar.

![Yeni Proje ekranı](media/project-creation-screen.png)

## <a name="configuring-your-new-project"></a>Yeni Project yapılandırma

Bir proje şablonu seçtikten sonra, aşağıdaki ekranlar projeyi ayarlamak için gereken yapılandırma adımlarında size kılavuzluk eder; Bu, proje türüne göre farklılık gösterebilir.

Tüm projeler, dosyaları depolamak için bir konum ile birlikte yeni bir proje gerektirir. Proje, var olan bir çözüme eklemek yerine yeni bir çözümün parçasıysa, bir çözüm adı da gerekecektir.

İsteğe bağlı olarak, bu aşamada git kaynak denetimi seçeneklerini de yapılandırabilirsiniz. Aşağıdaki görüntü, .NET Core projesi için son yapılandırma adımının bir örneğidir:

![Yeni bir proje yapılandırma](media/configure-new-project.png)

## <a name="adding-additional-projects-to-a-solution"></a>Çözüme ek projeler ekleme

çözüm **penceresinde** çözüme sağ tıklayıp **ekle > yeni Project** ekle veya ekle **> var olan Project** ekle ' yi seçerek başka projeler ekleyebilirsiniz.

Yeni bir proje eklemek, [yeni Project yapılandırma](#configuring-your-new-project)bölümünde gösterildiği gibi proje oluşturma aracılığıyla sizi ele alır.

Mevcut bir projeyi eklemeyi seçtiğinizde, makinenizde var olan bir projeye gözatmanıza ve bunu çözüme eklemenize olanak tanır.

## <a name="see-also"></a>Ayrıca bkz.

- [çözümler ve projeler oluşturma (Windows Visual Studio)](/visualstudio/ide/creating-solutions-and-projects)
