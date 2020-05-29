---
title: Yeni projeler ve çözümler oluşturma
description: Bu makalede Mac için Visual Studio ' de projelerin ve çözümlerin nasıl oluşturulacağı açıklanmaktadır
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/23/2019
ms.assetid: 5880BB10-0A12-47E2-8A82-7A2D59C4D579
ms.openlocfilehash: fa77993892c79cf29d268aa942b8c77ccb7a2139
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84183969"
---
# <a name="create-a-new-project"></a>Yeni bir proje oluştur

## <a name="opening-the-project-creation-dialog"></a>Proje oluşturma Iletişim kutusunu açma

Mac için Visual Studio yeni bir proje oluşturmanın birkaç yolu vardır. Mac için Visual Studio ilk kez açtığınızda başlangıç penceresi gösterilir. Buradan proje oluşturma ekranına kadar **Yeni** bir seçim yapabilirsiniz.

> [!TIP]
> Ayrıca, başlangıç penceresinde, son projeler ve çözümler için de açabilir ve arama yapabilirsiniz. Son projeleri de menü çubuğuna gidip **dosya > son çözümler** ' i seçerek açabilirsiniz.

![Yeni proje oluştur ile başlangıç penceresi](media/first-run-project.png)

Mac için Visual Studio yüklenmiş bir çözümle zaten açıksa, menü çubuğuna gidip **dosya > yeni çözüm**' i seçerek yeni bir çözüm oluşturabilirsiniz. Bu şekilde yeni bir çözüm oluşturulması, zaten yüklü olan çözümü kapatır.

## <a name="creating-a-new-project"></a>Yeni bir proje oluşturma

Varsayılan olarak **Yeni proje** iletişim kutusu, son kullanılan şablonlarınızı *en son*Kullanılanlar tarafından sıralanan şekilde gösterir.

Son kullanılan bir şablonu kullanmak istemiyorsanız, iletişim kutusunun solundaki kategoriler arasından seçim yapabilirsiniz. Her kategori, aralarından seçim yapabileceğiniz çeşitli proje şablonları içerir. Proje türüne tıklanması, ekranın sağ tarafında bir açıklama görmenizi sağlar.

![Yeni Proje ekranı](media/project-creation-screen.png)

## <a name="configuring-your-new-project"></a>Yeni projenizi yapılandırma

Bir proje şablonu seçtikten sonra, aşağıdaki ekranlar projeyi ayarlamak için gereken yapılandırma adımlarında size kılavuzluk eder; Bu, proje türüne göre farklılık gösterebilir.

Tüm projeler, dosyaları depolamak için bir konum ile birlikte yeni bir proje gerektirir. Proje, var olan bir çözüme eklemek yerine yeni bir çözümün parçasıysa, bir çözüm adı da gerekecektir.

İsteğe bağlı olarak, bu aşamada git kaynak denetimi seçeneklerini de yapılandırabilirsiniz. Aşağıdaki görüntü, .NET Core projesi için son yapılandırma adımının bir örneğidir:

![Yeni bir proje yapılandırma](media/configure-new-project.png)

## <a name="adding-additional-projects-to-a-solution"></a>Çözüme ek projeler ekleme

Çözüm Bölmesi çözüme sağ tıklayıp **Yeni proje ekle > Ekle** veya Ekle **> var olan proje**Ekle ' yi seçerek başka projeler ekleyebilirsiniz.

Yeni bir proje eklendiğinde, [yeni projenizi yapılandırma](#configuring-your-new-project)bölümünde gösterildiği gibi proje oluşturma boyunca işlem yapılır.

Mevcut bir projeyi eklemeyi seçtiğinizde, makinenizde var olan bir projeye gözatmanıza ve bunu çözüme eklemenize olanak tanır.

## <a name="see-also"></a>Ayrıca bkz.

- [Çözümler ve projeler oluşturma (Windows üzerinde Visual Studio)](/visualstudio/ide/creating-solutions-and-projects)
