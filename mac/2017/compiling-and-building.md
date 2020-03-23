---
title: Derleme ve Oluşturma
description: Bu makalede, Mac için Visual Studio'da nasıl derleyip proje ve çözümler üretilir
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: FB253757-DB00-4889-A6BF-E44722E25BD1
ms.openlocfilehash: 0165594b4c2d77005c2a9ef921cce457f6f2d0f6
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "74983610"
---
# <a name="compiling-and-building-in-visual-studio-for-mac"></a>Mac için Visual Studio'da derleme ve oluşturma

Mac için Visual Studio, projenizin geliştirilmesi sırasında uygulamalar oluşturmak ve derlemeler oluşturmak için kullanılabilir. Türü uyuşmazlıklarını ve diğer derleme zamanı hatalarını tanımlayabilmeniz için kodunuzu erken ve sık sık derlemeniz ve oluşturmanız önemlidir.

## <a name="building-from-the-ide"></a>IDE'den bina

Visual Studio for Mac'i kullanmak, yapı oluşturmanızı ve çalıştırmanızı anında sağlarken, yapı işlevselliği üzerinde denetim sağlar. Mac için Visual Studio, altta yatan yapı sistemi olarak MSBuild'i kullanır.

IDE'de oluşturulan tüm Projeler ve Çözümler, yapılar bağlamını tanımlayan varsayılan bir yapı yapılandırmasına sahip olacaktır. Bu yapılandırmalar düzenlenebilir veya kendi yapılandırmanızı oluşturabilirsiniz. Bu yapılandırmaları oluşturmak veya değiştirmek, projenizi oluşturmak için MSBuild tarafından kullanılan proje dosyasını otomatik olarak günceller.

IDE'de proje ve çözümlerin nasıl inşa edileöğretilenhakkında daha fazla bilgi [için, Proje ve Çözümler Oluşturma ve Temizleme](building-and-cleaning-projects-and-solutions.md) kılavuzuna bakın.

Mac için Visual Studio da aşağıdakileri yapmak için kullanılabilir:

* Çıktı yolunu değiştirin. Bu, Projenizin seçeneklerinde düzenlenir:

    ![Çıktı yolunu değiştirme](media/compiling-and-building-image4.png)

* Yapı çıktısının ayrıntılılığını değiştirin:

    ![Yapı ayrıntılılığını değiştirme](media/compiling-and-building-image5.png)

* Bina veya Temizleme den önce, sırasında veya sonrasında Özel Komutlar ekleyin:

    ![özel komutlar ekleme](media/compiling-and-building-image6.png)

## <a name="building-from-command-line"></a>Komut satırından bina

Komut satırı üzerinden uygulama oluşturmak için MSBuild Build Engine'i kullanabilirsiniz.

MSBuild'i kullanma hakkında daha fazla bilgi için [MSBuild](/visualstudio/msbuild/msbuild) içeriğine bakın.

## <a name="building-from-azure-pipelines"></a>Azure Boru Kaynaklarından Bina

* [Xamarin Uygulamanızı Oluşturun](/vsts/pipelines/apps/mobile/xamarin?view=vsts&tabs=vsts)
* [Xamarin ile Sürekli Entegrasyon](https://developer.xamarin.com/guides/cross-platform/ci/)

## <a name="see-also"></a>Ayrıca bkz.

- [Derleme ve oluşturma (Windows'ta Visual Studio)](/visualstudio/ide/compiling-and-building-in-visual-studio)