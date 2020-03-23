---
title: Derleme ve Oluşturma
description: Bu makalede, Mac için Visual Studio'da nasıl derleyip proje ve çözümler üretilir
ms.topic: overview
author: heiligerdankgesang
ms.author: dominicn
ms.date: 08/29/2019
ms.assetid: FB253757-DB00-4889-A6BF-E44722E25BD1
ms.openlocfilehash: b4f1cfc3dfdffcc3dd4cb90cd7d29d4333578b9a
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "71128414"
---
# <a name="compiling-and-building-in-visual-studio-for-mac"></a>Mac için Visual Studio'da derleme ve oluşturma

Mac için Visual Studio, projenizin geliştirilmesi sırasında uygulamalar oluşturmak ve derlemeler oluşturmak için kullanılabilir. Tür uyuşmazlıklarını, hatalı sözdizimini, yanlış yazılmış anahtar kelimeleri ve diğer derleme zamanı hatalarını hızlı bir şekilde belirlemenize olanak sağlamak için kodunuzu sık sık oluşturmak önemlidir. Daha sonra hata ayıklama oluşturarak, mantık, IO ve sıfıra bölme hataları gibi çalışma zamanı hatalarını bulabilir ve düzeltebilirsiniz.

Başarılı bir yapı, kaynak kodunun doğru sözdizimi içerdiği ve kitaplıklara, derlemelere ve çözümlenebilecek diğer bileşenlere yapılan tüm statik başvuruları içerdiği anlamına gelir. Yapı işlemi yürütülebilir bir uygulama üretir. Bu yürütülebilir sonra hata ayıklama ve kod kalitesini doğrulamak için manuel ve otomatik testlerin farklı türleri ile sınanabilir. Uygulamanız tam olarak sınandıktan sonra, müşterilerinize dağıtmak için bir sürüm sürümü derleyebilirsiniz.

Mac'te, uygulamanızı oluşturmak için aşağıdaki yöntemlerden herhangi birini kullanabilirsiniz: Mac için Visual Studio, MSBuild komut satırı araçları veya Azure Ardışık Hatları.

| Yapı Yöntemi | Avantajlar |
| --- |--- | --- |
| Mac için Visual Studio |- Hemen oluşturur oluşturun ve bir hata ayıklama onları test edin.<br />- C# projeleri için çok işlemcili yapılar çalıştırın.<br />- Yapı sisteminin farklı yönlerini özelleştirin. |
| MSBuild komut satırı| - Mac için Visual Studio yüklemeden projeler oluşturun.<br />- Tüm proje türleri için çok işlemcili yapılar çalıştırın.<br />- Yapı sisteminin çoğu alanını özelleştirin.|
| Azure Pipelines | - Sürekli entegrasyon/sürekli teslimat boru hattının bir parçası olarak yapı sürecinizi otomatikleştirin.<br />- Her yapıya otomatik testler uygulayın.<br />- Yapı işlemleri için neredeyse sınırsız bulut tabanlı kaynak yararlanın.<br />- Yapı iş akışını değiştirin ve derinden özelleştirilmiş görevleri gerçekleştirmek için yapı etkinlikleri oluşturun.|

Bu bölümdeki belgeler, IDE tabanlı yapı sürecinin daha ayrıntılı olarak gider. Komut satırı üzerinden uygulama oluşturma hakkında daha fazla bilgi için [MSBuild'e](/visualstudio/msbuild/msbuild)bakın. Azure Pipelines ile uygulama oluşturma hakkında daha fazla bilgi için [Azure Ardışık Hatları'na](/azure/devops/pipelines)bakın.


> [!NOTE]
> Bu konu Mac için Visual Studio için geçerlidir. Windows'daki Visual Studio için [Derleme'ye bakın ve Visual Studio'da oluşturun.](/visualstudio/ide/compiling-and-building-in-visual-studio)


## <a name="building-from-the-ide"></a>IDE'den bina

Mac için Visual Studio, yapı oluşturmanızı ve çalıştırmanızı sağlarken, yapı işlevselliği üzerinde denetim sağlar. Bir proje oluşturduğunuzda, Mac için Visual Studio, yapılar için bağlamı ayarlayan varsayılan bir yapı yapılandırması tanımlar. Varsayılan yapı yapılandırmalarını düzenleme yapabilir ve kendi yapılandırmanızı da oluşturabilirsiniz. Bu yapılandırmaları oluşturmak veya değiştirmek, projenizi oluşturmak için MSBuild tarafından kullanılan proje dosyasını otomatik olarak günceller.

IDE'de proje ve çözümlerin nasıl inşa edileöğretilenhakkında daha fazla bilgi [için, Proje ve Çözümler Oluşturma ve Temizleme](building-and-cleaning-projects-and-solutions.md) kılavuzuna bakın.

Mac için Visual Studio da aşağıdakileri yapmak için kullanılabilir:

* Çıktı yolunu değiştirin. Bu, Projenizin seçeneklerinde düzenlenir:

    ![Çıktı yolunu değiştirme](media/compiling-and-building-image4.png)

* Yapı çıktısının ayrıntılılığını değiştirin:

    ![Yapı ayrıntılılığını değiştirme](media/compiling-and-building-image5.png)

* Bina veya Temizleme den önce, sırasında veya sonrasında Özel Komutlar ekleyin:

    ![özel komutlar ekleme](media/compiling-and-building-image6.png)


## <a name="see-also"></a>Ayrıca bkz.

- [Derleme ve oluşturma (Windows'ta Visual Studio)](/visualstudio/ide/compiling-and-building-in-visual-studio)
