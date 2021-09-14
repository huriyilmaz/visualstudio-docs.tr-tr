---
title: Çeşitli dosyalar
description: Visual Studio bir projede veya çözümde bulunmayan dosyalar üzerinde nasıl çalışacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.newfile
- VS.OpenWith
- MiscellaneousFilesProject
helpviewer_keywords:
- solutions, miscellaneous files
- standalone files
- Solution Explorer, miscellaneous files
- Miscellaneous Files folder
- files [Visual Studio], miscellaneous
ms.assetid: 5b96640b-8efe-48a4-8d0a-1ae3f9587e44
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: db9b62e2e3135045c2a4a822585f2e69fe85b02a
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628724"
---
# <a name="miscellaneous-files"></a>Çeşitli dosyalar

dosya üzerinde bir proje veya çözümden bağımsız olarak çalışmak için Visual Studio düzenleyicisini kullanmak isteyebilirsiniz. Açık bir çözümünüz varsa, dosyaları bir çözüme veya bir projeye eklemeden açabilir ve değiştirebilirsiniz. Bağımsız olarak çalışmak istediğiniz dosyalara çeşitli dosyalar denir. Çeşitli dosyalar, çözümlerin ve projelerin dışında, yapılara dahil edilmez ve kaynak denetimi altında bir çözüme dahil edilemez.

Dosyaları bir projeden veya çözümden bağımsız olarak açmak çeşitli nedenlerden dolayı faydalıdır. Proje tabanlı bir çözüm geliştirirken görüntülemek istediğiniz bir dosyanız olabilir ancak bu, çözümün geliştirmesi için ayrılmaz değildir. Ortak örneklerde geliştirme notları veya yönergeleri, veritabanı şeması ve kod klipleri verilebilir. Ayrıca, tek başına bir dosya oluşturmak isteyebilirsiniz.

![Çözüm projeleri](../../ide/reference/media/projects_solutions_misc.gif)

Çözüm Gezgini, klasör seçenekleri etkinleştirilmişse dosyalar için **çeşitli dosyalar** klasörünü gösterebilir. Seçenekler [Belgeler, ortam, Seçenekler Iletişim kutusundan](../../ide/reference/documents-environment-options-dialog-box.md)ayarlanabilir. Çeşitli bir dosyayı kapattıktan sonra, bir seçenek de etkinleştirilmediği sürece belirli bir çözümle veya projeyle ilişkili değildir.

**Miscellaneous Files** klasörü, dosyaları bağlantı olarak temsil eder. Bu klasör bir çözümün parçası olmasa da, bir çözümü açtığınızda, klasör ayarlarına bağlı olarak çözüm son kapatıldığı sırada açılan bazı veya tüm dosyalar yeniden açılır.

> [!NOTE]
> **Çeşitli dosyalar** klasöründe görünmeyen dosyalardan bazıları, .zip dosyaları ve .doc dosyaları gibi IDE içinde değiştiremeyeceğiniz dosyalardır. IDE yalnızca harici bir düzenleyici aracılığıyla değiştirilebilen dosyaları izlemez.

## <a name="commands-available-in-the-ide"></a>IDE 'de kullanılabilen komutlar

Menüler, araç çubukları ve içerdikleri komutlar, açtığınız dosyanın biçimine göre değişir. Örneğin, metin düzenleyici araç çubuğu göründüğünde ve komutları kullanılabilir olduğunda bir metin dosyası açtığınızda. Daha sonra bir XML şema dosyası açarsanız, XML Şeması araç çubuğu görüntülenir. XML şemanız düzenlenirken, metin düzenleyici araç çubuğunun komutları (veya araç çubuğunun kendisi) kullanılamaz. XML şeması etkin pencere ve bu nedenle geçerli seçim bağlamına sahiptir. Bir proje dosyası ve çeşitli bir dosya arasında geçiş yaptığınızda, projeyle ilgili tüm komutlar kaybolur ve yalnızca çeşitli dosya ile ilgili olanlar görüntülenir.

## <a name="folder-display-options"></a>Klasör görüntüleme seçenekleri

Diğer **dosyalar** klasörünün görüntüleme seçeneklerini, başka bir dosya açmış olsanız da klasörün görünmesini sağlayacak şekilde ayarlayabilirsiniz. Çözüm dosyası çeşitli dosyaların bir listesini kalıcı olarak yönetmez. Bu, kullanıcının Kullanıcı başına, son kullanılan (MRU) dosya listesini anımsamasını sağlayan isteğe bağlı bir özellik kullanır.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio’da projeler veya çözümler olmadan kod geliştirme](../develop-code-in-visual-studio-without-projects-or-solutions.md)
- [Çözümler ve projeler](../../ide/solutions-and-projects-in-visual-studio.md)
- [Belgeler, Ortam, Seçenekler İletişim Kutusu](../../ide/reference/documents-environment-options-dialog-box.md)
