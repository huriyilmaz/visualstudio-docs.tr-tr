---
title: Seçenekler İletişim Kutusu, Projeler ve Çözümler, Derleme ve Çalıştırma
ms.date: 07/14/2017
ms.technology: vs-ide-compile
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Projects.Build_and_Run
helpviewer_keywords:
- builds [Visual Studio], setting up
- run actions
- debugger, run options
ms.assetid: c884976e-c0df-4c6d-8e3a-856ea2bd547c
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 24ba5bbf34ecc12c2508c538e74909ee0a10aef4
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "68461386"
---
# <a name="options-dialog-box-projects-and-solutions--build-and-run"></a>Seçenekler iletişim kutusu: Projeler \> ve Çözümler Oluştur ve Çalıştır

Bu iletişim kutusunda, aynı anda oluşturabilecek maksimum C++ veya C# projesi sayısını, belirli varsayılan yapı davranışlarını ve bazı yapı günlüğü ayarlarını belirtebilirsiniz. Bu seçeneklere erişmek **için, Araçlar** >  **Seçenekleri'ni seçin Projeleri ve Çözümleri**genişletin ve ardından Oluştur ve **Çalıştır'ı**seçin.**Options**

**Maksimum paralel proje oluşturma sayısı**

Aynı anda oluşturabilecek maksimum C++ ve C# proje sayısını belirtir. Yapı işlemini en iyi duruma getirmek için, en fazla paralel proje oluşturma sayısı otomatik olarak bilgisayarınızın CPU sayısına ayarlanır. Maksimum değer 32'dir.

**Yalnızca Başlangıç projeleri ve Run'a bağımlılıklar oluşturun**

**F5** anahtarını, **Hata Ayıklama** > **Hata Ayıklama** menüsü komutunu veya **Yapı** menüsündeki geçerli komutları kullandığınızda yalnızca başlangıç projesini ve bağımlılıklarını oluşturur. İşaretlenmemişse, tüm projeler ve bağımlılıklar oluşturulur.

**Run'da, projeler güncel olmadığında**

*Yalnızca C++ projeleri için geçerlidir.*

**F5** veya **Hata Ayıklama** > **Başlangıç Hata Ayıklama** komutu yla bir proje çalıştırırken, proje yapılandırması güncel değilse, oluşturmak için varsayılan ayar Komut **İstemi** bir ileti görüntüler. Her çalıştırılışta projeyi oluşturmak için **Her Zaman oluştur'u** seçin. Proje çalıştırıldığında tüm otomatik yapıları bastırmak için **Asla oluştur'u** seçin.

**Run'da, yapı veya dağıtım hataları oluştuğunda**

*Yalnızca C++ projeleri için geçerlidir.*

**F5** veya **Hata Ayıklama** > **Başlangıç Hata Ayıklama** komutu ile bir proje çalıştırırken, yapı başarısız olsa bile bir proje çalıştırılmak gerekirse başlatmak için varsayılan ayar **Komut Istemi** bir ileti görüntüler. Son iyi yapıyı otomatik olarak başlatmak için **eski sürümü başlat'ı** seçin ve bu da çalışan kod la kaynak kodu arasında uyumsuzluklara neden olabilir. İletiyi bastırmak için **başlatMayın'ı** seçin.

**Yeni çözümler için başlangıç projesi olarak şu anda seçili projeyi kullanın**

Bu seçenek ayarlandığında, yeni çözümler başlangıç projesi olarak şu anda seçili projeyi kullanır.

**MSBuild projesi çıkış ayrıntılılığı oluşturmak**

Oluşturma işleminden ne kadar bilginin **Çıktı** penceresinde görüntüleneceğini belirler.

**MSBuild proje oluşturma günlüğü dosyası ayrıntılı**

*Yalnızca C++ projeleri için geçerlidir.*

* \\ \<ProjectName>\Debug\\\<ProjectName>.log*adresinde bulunan yapı günlüğü dosyasına ne kadar bilgi yazıldığını belirler.

## <a name="see-also"></a>Ayrıca bkz.

- [Derleme ve Oluşturma](../../ide/compiling-and-building-in-visual-studio.md)
- [Seçenekler İletişim Kutusu, Projeler ve Çözümler](projects-and-solutions-options-dialog-box.md)
- [Seçenekler İletişim Kutusu, Projeler ve Çözümler, Web Projeleri](options-dialog-box-projects-and-solutions-web-projects.md)