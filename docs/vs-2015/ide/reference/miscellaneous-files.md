---
title: Çeşitli dosyalar | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.newfile
- VS.OpenWith
- MiscellaneousFilesProject
helpviewer_keywords:
- solutions, miscellaneous files
- builds [Visual Studio], miscellaneous files
- standalone files
- Solution Explorer, miscellaneous files
- Miscellaneous Files folder
- files [Visual Studio], outside of containers
- files [Visual Studio], Miscellaneous Files folder
ms.assetid: 5b96640b-8efe-48a4-8d0a-1ae3f9587e44
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8dc11714fc8b2d5a345d94ddfe4c5de2c2cd7fe5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72666860"
---
# <a name="miscellaneous-files"></a>Çeşitli Dosyalar
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]Düzenleyicilerin bir projeden veya bir çözümden dosyalar üzerinde bağımsız olarak çalışmak için kullanmak isteyebilirsiniz. Açık bir çözümünüz varsa, dosyaları bir çözüme veya bir projeye eklemeden açabilir ve değiştirebilirsiniz. Kapsayıcılardan bağımsız olarak çalışmak istediğiniz dosyalara çeşitli dosyalar denir. Çeşitli dosyalar, çözümlerin ve projelerin dışında, yapılara dahil edilmez ve kaynak denetimi altında bir çözüme dahil edilemez.

 Dosyaları kapsayıcıdan bağımsız olarak açmak çeşitli nedenlerden dolayı faydalıdır. Proje tabanlı bir çözüm geliştirirken görüntülemek istediğiniz bir dosyanız olabilir ancak bu, çözümün geliştirmesi için ayrılmaz. Ortak örneklerde geliştirme notları veya yönergeleri, veritabanı şeması ve kod klipleri verilebilir. Ayrıca, tek başına bir dosya oluşturmak isteyebilirsiniz.

 ![Çözüm projeleri](../../ide/reference/media/projects-solutions-misc.gif "Projects_Solutions_Misc")

 Çözüm Gezgini, klasör seçenekleri etkinleştirilmişse dosyalar için çeşitli dosyalar klasörünü gösterebilir. Seçenekler [Belgeler, ortam, Seçenekler Iletişim kutusundan](../../ide/reference/documents-environment-options-dialog-box.md)ayarlanabilir. Çeşitli bir dosyayı kapattıktan sonra, bir seçenek de etkinleştirilmediği sürece belirli bir çözümle veya projeyle ilişkili değildir.

 Miscellaneous Files klasörü, dosyaları bağlantı olarak temsil eder. Bu klasör bir çözümün parçası olmasa da, bir çözümü açtığınızda, çözüm son kapatıldığında açılan bazı veya tüm dosyalar, klasörün ayarlarına bağlı olarak yeniden açılır.

> [!NOTE]
> Çeşitli dosyalar klasöründe görünmeyen dosyalardan bazıları. zip dosyaları ve. doc dosyaları gibi IDE içinde değiştiremeyeceğiniz dosyalardır. IDE yalnızca harici bir düzenleyici aracılığıyla değiştirilebilen dosyaları izlemez.

## <a name="commands-available-in-the-ide"></a>IDE 'de kullanılabilen komutlar
 Menüler, araç çubukları ve içerdikleri komutlar, açtığınız dosyanın biçimine göre değişir. Örneğin, metin düzenleyici araç çubuğu göründüğünde ve komutları kullanılabilir olduğunda bir metin dosyası açtığınızda. Daha sonra bir XML şema dosyası açarsanız, XML Şeması araç çubuğu görüntülenir. XML şemanız düzenlenirken, metin düzenleyici araç çubuğunun komutları (veya araç çubuğunun kendisi) kullanılamaz. XML şeması etkin pencere ve bu nedenle geçerli seçim bağlamına sahiptir. Bir proje dosyası ve çeşitli bir dosya arasında geçiş yaptığınızda, projeyle ilgili tüm komutlar kaybolur ve yalnızca çeşitli dosya ile ilgili olanlar görüntülenir.

## <a name="folder-display-options"></a>Klasör görüntüleme seçenekleri
 Çeşitli dosyaları açmış olsanız da, klasör görünecek şekilde çeşitli klasörler için görüntüleme seçeneklerini ayarlayabilirsiniz. Çözüm dosyası çeşitli dosyaların bir listesini kalıcı olarak yönetmez. Bu, kullanıcının Kullanıcı başına en son kullanılan (MRU) dosya listesini anımsamasını sağlayan isteğe bağlı bir özellik kullanır.

## <a name="see-also"></a>Ayrıca Bkz.
 [Çözümler ve projeler](../../ide/solutions-and-projects-in-visual-studio.md) [Belgeler, ortam, Seçenekler iletişim kutusu](../../ide/reference/documents-environment-options-dialog-box.md)
