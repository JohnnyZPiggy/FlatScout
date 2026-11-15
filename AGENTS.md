# 租房清单与草稿规则（每次运行均遵守）
- 居住人数：夫妻两人；两人均须能合法居住并正式登记居留；仅长期正式租约，排除合租、短租、转租。
- 地区同等考虑：Saint-Sulpice、Ecublens、Chavannes-près-Renens、Lausanne 西部、Renens、Crissier 及交通方便的周边；含 charges 总租金 CHF 800–1400，超出不收录。
- 1.5 pièces 优先；明显合适时收录 1–2.5 pièces 并备注房型风险；1.5 pièces 两人入住风险较高，listings.csv 备注须写“两人入住待确认”，邮件须明确询问。
- 不编造信息，未知字段留空；保留来源、链接、发现及核实日期、状态，按链接去重且不删除历史；老广告或仅能打开页面不能标可租，未确认可申请标“未核实”，已下架标“已下架”。
- 沿用之前清单规则：仅复核超过24小时且未下架的旧记录，价格或状态变化备注旧值；CSV 保持 UTF-8 BOM；无法访问须汇报“本轮未能访问”，不可用摘要替代页面。
- 每轮最多5套草稿；不发邮件、不提交申请；不写个人姓名、电话、证件、收入，不附附件；草稿结尾保留署名占位符。
- 所有邮件均逐字使用以下夫妻两人法语模板，按房源替换占位符并保留段落空行；邮件日期须为法语（如 1er février 2027），不得用 ISO 日期；文件名沿用日期_地址.txt，已有文件名不变。
Objet : Demande de renseignements et de visite — {adresse} (réf. {référence})
Madame, Monsieur,
Nous sommes un couple et nous recherchons un logement dans la région de l’EPFL et de l’UNIL pour nous y installer durablement. Votre appartement de {pièces} pièce(s) situé à {adresse complète} (référence {référence}) nous intéresse.
Est-il toujours disponible à la location et acceptez-vous encore des demandes ? Le logement peut-il être occupé par deux personnes, et proposez-vous un bail officiel de longue durée permettant à chacun de s’inscrire officiellement auprès du contrôle des habitants ? Pourriez-vous également confirmer le loyer mensuel total de CHF {total}, charges comprises, et la date d’entrée ({date en français}) ?
Serait-il possible d’organiser une visite ? Nous vous remercions de bien vouloir nous indiquer les créneaux disponibles.
Avec nos salutations distinguées,
[署名由发件人补充]
