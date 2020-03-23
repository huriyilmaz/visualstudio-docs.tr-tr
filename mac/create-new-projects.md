---
title: Yeni Projeler ve Çözümler Oluşturma
description: Bu makalede, Mac için Visual Studio'da nasıl proje ve çözüm oluşturulacak açıklanmaktadır
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/23/2019
ms.assetid: 5880BB10-0A12-47E2-8A82-7A2D59C4D579
ms.openlocfilehash: 10fcb52a8e1311f3e8128361ee835f6ddcb3670d
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "75678915"
---
# <a name="create-a-new-project"></a>Yeni Bir Proje Oluştur

## <a name="opening-the-project-creation-dialog"></a>Proje Oluşturma İletişim kutusunu açma

Mac için Visual Studio'da yeni bir proje oluşturmanın birkaç yolu vardır. Mac için Visual Studio'yu ilk açtığınızda, başlangıç penceresi gösterilir. Buradan sizi proje oluşturma ekranına götüren **Yeni'yi** seçebilirsiniz.

> [!TIP]
> Ayrıca, başlangıç penceresinden, son projeleri ve çözümleri de açıp arayabilirsiniz. Ayrıca menü çubuğuna giderek ve Son Çözümler **> Dosya'yı** seçerek son projeleri de açabilirsiniz

![Yeni proje oluşturma ile pencereyi başlat](media/first-run-project.png)

Mac için Visual Studio zaten yüklü bir çözüm ile açıksa, menü çubuğuna giderek ve **Yeni Çözüm > Dosya**seçerek yeni bir çözüm oluşturabilirsiniz. Bu şekilde yeni bir çözüm oluşturmak zaten yüklenmiş olan çözümü kapatır.

## <a name="creating-a-new-project-from-a-template"></a>Şablondan Yeni Proje Oluşturma

**Yeni Proje** iletişim kutusu, varsayılan olarak, en son kullanılan şablonlarınızı en *son kullanılana*göre sıralanır şekilde gösterir.

Yeni bir şablon kullanmak istemiyorsanız, iletişim kutusunun solundaki kategorilerarasından seçim yapabilirsiniz. Her kategori, aralarından seçim yapabileceğiniz birkaç proje şablonu içerir. Proje türüne tıkladığınızda ekranın sağ tarafında bir açıklama görmenizi sağlar.

![Yeni proje ekranı](media/project-creation-screen.png)

## <a name="configuring-your-new-project"></a>Yeni Projenizi Yapılandırma

Bir proje şablonu seçtikten sonra, aşağıdaki ekranlar projeyi ayarlamak için gereken yapılandırma adımlarını size iletir; bu proje türüne göre değişebilir.

Tüm projeler, dosyaları depolamak için bir konumla birlikte yeni bir proje gerektirir. Proje, varolan bir çözüme eklemek yerine yeni bir çözümün parçasıysa, bir çözüm adı da gerekir.

İsteğe bağlı olarak, bu aşamada Git kaynak denetim seçeneklerini de yapılandırabilirsiniz. Aşağıdaki resim, bir .NET Core projesi için son yapılandırma adımının bir örneğidir:

![Yeni bir projeyi yapılandırma](media/configure-new-project.png)

## <a name="adding-additional-projects-to-a-solution"></a>Çözüme Ek Proje Ekleme

Çözüm Defteri'ndeki çözüme sağ tıklayarak ve **Yeni Proje Ekle >** veya **Varolan Proje**Ekle > ekle seçeneğini seçerek çözüme ek projeler ekleyebilirsiniz.

Yeni projeekleme, [Yeni Projenizi Yapılandırmada](#configuring-your-new-project)gösterildiği gibi, proje oluşturma yoluyla götürecektir.

Varolan bir proje eklemeyi seçmek, makinenizdeki varolan bir projeye göz atmanızı ve çözüme eklemenize olanak sağlar.

## <a name="see-also"></a>Ayrıca bkz.

- [Çözümler ve projeler oluşturun (Windows'ta Visual Studio)](/visualstudio/ide/creating-solutions-and-projects)
