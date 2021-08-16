---
title: Kaynak denetim bilgisini. proj ve. sln dosyalarından kaldır
description: Kaynak denetimi eklentisi API 'sinde, SCC bilgileri bir MSSCCPRJ depolanır. Proje ve çözüm dosyaları yerine SCC dosyası.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, .sln and .proj files
ms.assetid: 7b06883f-35de-41e2-9a9e-d3edba236f17
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 2107c9523b3d9d5c96db273e1f39a8feb687d59aa917752e2875d8be4a223bfe
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121414460"
---
# <a name="removal-of-source-control-information-from-proj-and-sln-files"></a>Kaynak denetim bilgilerinin. proj ve. sln dosyalarından kaldırılması

Kaynak denetimi eklentisi API 'sinin sürüm 1,2 ' de, SCC bilgileri bir MSSCCPRJ depolanır. SCC dosyası. MSSCCPRJ avantajı. SCC dosyası. proj ve. sln dosyalarında olduğu gibi, SCC bilgisinin kaynak denetimli olmaması olabilir.

## <a name="version-12-changes"></a>Sürüm 1,2 değişiklikleri

 Kaynak denetimi eklentisi API sürüm 1,1 ' i temel alan kaynak denetimi eklentilerinde, kaynak denetimi ile ilgili bilgiler proje (. proj) ve çözüm (. sln) dosyalarında depolanır. Kaynak denetim bilgisinin veritabanı konumu AuxPath tarafından belirtilir ve veritabanı içindeki belirli konum ProjName tarafından belirtilir. Bu davranış, bu işlemlerden herhangi biri sonrasında ProjName genellikle geçersiz olacağından, dal, çatal veya kopyalama işlemlerinden sonra sorunlara yol açabilir.

 Kaynak denetimi eklentisi API sürümü 1,1 ' de, IDE, bir eklentinin MSSCCPRJ tarafından desteklenip desteklenmediğini algılamak için ~ SAK dosyalarını kullandı. Kaynak denetim bilgilerini depolamanın SCC yöntemi. Kaynak denetimi eklentisi API sürümü 1,2, MSSCCPRJ desteğini algılamaya yönelik yeni bir özellik sunar. Bir ~ SAK dosyası kullanmadan SCC dosyası. Daha fazla bilgi için bkz. yok [~ sak Files](../../extensibility/internals/elimination-of-tilde-sak-files.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Kaynak Denetimi Eklentisi API Sürümü 1.2’deki Yenilikler](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
