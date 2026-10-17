# PM Tools / 项目工具
---

```dataviewjs
// =============================================================
// PM Tools — 与 Main Board 同目录的辅助工具页
// =============================================================

const BOARD_PATH = "Boards/Main Board.md";
const CARD_DIR   = "Cards";
const TEMPLATE_PATH = "Templates/card.md";

// ---- 轻量拼音字典（覆盖 PM 项目名常用字） ----
const PY = {"了":"le","我":"wo","你":"ni","他":"ta","她":"ta","它":"ta","们":"men","的":"de","是":"shi","在":"zai","有":"you","和":"he","不":"bu","一":"yi","也":"ye","都":"dou","就":"jiu","说":"shuo","要":"yao","看":"kan","能":"neng","到":"dao","去":"qu","来":"lai","做":"zuo","给":"gei","把":"ba","让":"rang","着":"zhe","过":"guo","下":"xia","上":"shang","这":"zhe","那":"na","里":"li","还":"hai","没":"mei","很":"hen","多":"duo","少":"shao","大":"da","小":"xiao","好":"hao","新":"xin","旧":"jiu","高":"gao","低":"di","长":"chang","短":"duan","先":"xian","后":"hou","前":"qian","天":"tian","年":"nian","月":"yue","日":"ri","时":"shi","分":"fen","点":"dian","现在":"xianzai","今天":"jintian","明天":"mingtian","昨天":"zuotian","工作":"gongzuo","生活":"shenghuo","项目":"xiangmu","测试":"ceshi","音乐":"yinyue","视频":"shipin","解读":"jiedu","顶刊":"dingkan","混音":"hunyin","交响":"jiaoxiang","交响曲":"jiaoxiangqu","诺兰":"nuolan","创作":"chuangzuo","写作":"xiezuo","设计":"sheji","开发":"kaifa","研究":"yanjiu","分析":"fenxi","管理":"guanli","计划":"jihua","报告":"baogao","笔记":"biji","日记":"riji","日志":"rizhi","模板":"muban","目录":"mulu","文件":"wenjian","文档":"wendang","卡片":"kapian","看板":"kanban","音乐mv":"yinlemv","专辑":"zhuanji","制作":"zhizuo","录制":"luzhi","剪辑":"jianji","发布":"fabu","脚本":"jiaoben","歌词":"geci","作曲":"zuoqu","编曲":"bianqu","演唱":"yanchang","歌手":"geshou","歌名":"geming","节奏":"jiezou","旋律":"xuanlu","和声":"hesheng","混响":"hunxiang","效果":"xiaoguo","风格":"fengge","氛围":"fenwei","情绪":"qingxu","情感":"qinggan","感情":"ganqing","感觉":"ganjue","画面":"huamian","色彩":"secai","光线":"guangxian","镜头":"jingtou","场景":"changjing","故事":"gushi","剧情":"juqing","情节":"qingjie","人物":"renwu","角色":"juese","主角":"zhujue","配角":"peijue","电影":"dianying","电视剧":"dianshiju","动漫":"dongman","动画":"donghua","漫画":"manhua","小说":"xiaoshuo","散文":"sanwen","诗歌":"shige","文学":"wenxue","艺术":"yishu","科技":"keji","科学":"kexue","技术":"jishu","产品":"chanpin","功能":"gongneng","特点":"tedian","优势":"youshi","劣势":"lieshi","需求":"xuqiu","解决方案":"jiejuefangan","应用":"yingyong","评论":"pinglun","分享":"fenxiang","查看":"chakan","下载":"xiazai","上传":"shangchuan","删除":"shanchu","编辑":"bianji","保存":"baocun","取消":"quxiao","确认":"queren","返回":"fanhui","下一步":"xiayibu","完成":"wancheng","开始":"kaishi","结束":"jieshu","下午":"xiawu","上午":"shangwu","晚上":"wanshang","早上":"zaoshang","中午":"zhongwu","凌晨":"lingchen","周末":"zhoumo","周末":"zhoumo","星期":"xingqi","周":"zhou","月":"yue","季度":"jidu","年":"nian","现在":"xianzai","之前":"zhiqian","之后":"zhihou","之间":"zhijian","左右":"zuoyou","上下":"shangxia","左右":"zuoyou","前后":"qianhou","里外":"liwai","内外":"neiwai","高低":"gaodi","长短":"changduan","大小":"daxiao","多少":"duoshao","快慢":"kuaiman","好坏":"haohuai","对错":"duicuo","真假":"zhenjia","新旧":"xinjiu","远近":"yuanjin","深浅":"shenqian","粗细":"cuxi","胖瘦":"pangshou","冷热":"lengre","甜咸":"tianxian","酸甜":"suatian","辛苦":"xinku","开心":"kaixin","快乐":"kuaile","幸福":"xingfu","健康":"jiankang","平安":"pingan","顺利":"shunli","成功":"chenggong","失败":"shibai","努力":"nuli","聪明":"congming","漂亮":"piaoliang","可爱":"keai","帅气":"shuaiqi","温柔":"wenrou","善良":"shanliang","友好":"youhao","诚实":"chengshi","谦虚":"qianxu","礼貌":"limao","尊重":"zunzhong","理解":"lijie","沟通":"goutong","表达":"biaoda","思考":"sikao","学习":"xuexi","成长":"chengzhang","进步":"jinbu","改变":"gaibian","突破":"tupo","挑战":"tiaozhan","机会":"jihui","问题":"wenti","答案":"daan","方法":"fangfa","步骤":"buzhou","原则":"yuanze","标准":"biaozhun","规则":"guize","制度":"zhidu","流程":"liucheng","技巧":"jiqiao","经验":"jingyan","知识":"zhishi","信息":"xinxi","数据":"shuju","版本":"banben","更新":"gengxin","升级":"shengji","维护":"weihu","修复":"xiufu","优化":"youhua","完善":"wanshan","技能":"jineng","提醒":"tixing","通知":"tongzhi","更新":"gengxin","新闻":"xinwen","报道":"baodao","会议":"huiyi","讨论":"taolun","决议":"jueyi","投票":"toupiao","选择":"xuanze","决定":"jueding","变更":"biangeng","归档":"guidang","记录":"jilu","查询":"chaxun","检索":"jiansuo","参考":"cankao","引用":"yinyong","来源":"laiyuan","链接":"lianjie","网址":"wangzhi","网站":"wangzhan","移动":"yidong","设备":"shebei","电脑":"diannao","手机":"shouji","平板":"pingban","相机":"xiangji","耳机":"erji","音箱":"yinxiang","屏幕":"pingmu","键盘":"jianpan","鼠标":"shubiao","网络":"wangluo","系统":"xitong","软件":"ruanjian","工具":"gongju","菜单":"caidan","按钮":"anniu","开关":"kaiguan","灯光":"dengguang","声音":"shengyin","音乐":"yinyue","节奏":"jiezou","节拍":"jiepai","速度":"sudu","音量":"yinliang","静音":"jingyin","播放":"bofang","暂停":"zanting","停止":"tingzhi","循环":"xunhuan","随机":"suiji","下一首":"xiayishou","上一首":"shangyishou","专辑":"zhuanji","曲目":"qumu","经典":"jingdian","电影":"dianying","预告片":"yugaopian","片头":"paitou","片尾":"pianwei","字幕":"zimu","配音":"peiying","原声":"yuansheng","特效":"texiao","后期":"houqi","概念":"gainian","风格":"fengge","主题":"zhuti","方向":"fangxiang","维度":"weidu","角度":"jiaodu","深度":"shendu","高度":"gaodu","广度":"guangdu","宽度":"kuandu","长度":"changdu","面积":"mianji","重量":"zhongliang","温度":"wendu","湿度":"shidu","比例":"bili","百分比":"baifenbi","分数":"fenshu","小数":"xiaoshu","整数":"zhengshu","数字":"shuzi","字母":"zimu","汉字":"hanzi","英文":"yingwen","中文":"zhongwen","日文":"riwen","韩文":"hanwen","法文":"fawen","德文":"dewen","西班牙文":"xibanyawen","俄文":"ewen","阿拉伯文":"alabowen","图标":"tubiao","表情":"biaoqing","符号":"fuhao","格式":"geshi","编码":"bianma","解码":"jiema","压缩":"yasuo","解压":"jieya","加密":"jiami","解密":"jiemi","备份":"beifen","恢复":"huifu","同步":"tongbu","上传":"shangchuan","下载":"xiazai","导入":"daoru","导出":"daochu","打印":"dayin","扫描":"saomiao","识别":"shibie","翻译":"fanyi","语音":"yuyin","视频":"shipin","图片":"tupian","照片":"zhaopian","录像":"luxiang","录音":"luyin","直播":"zhibo","会议":"huiyi","讲座":"jiangzuo","演讲":"yanjiang","汇报":"huibao","总结":"zongjie","回顾":"huigu","展望":"zhanwang","目标":"mubiao","任务":"renwu","进度":"jindu","成果":"chengguo","效果":"xiaoguo","反响":"fanxiang","反响":"fanxiang","海报":"haibao","封面":"fengmian","徽标":"huibiao","标志":"biaozhi","logo":"logo","图标":"tubiao","卡片":"kapian","看点":"kandian","截图":"jietu","片段":"pianduan","章节":"zhangjie","段落":"duanluo","行":"hang","列":"lie","文字":"wenzi","内容":"neirong","标题":"biaoti","副标题":"fubiaoti","正文":"zhengwen","脚注":"jiaozhu","页眉":"yeimei","页脚":"yejiao","目录":"mulu","索引":"suoyin","附录":"fulu","书签":"shuqian","标签":"biaoqian","分类":"fenlei","排序":"paixu","筛选":"shaixuan","搜索":"sousuo","推荐":"tuijian","热门":"remen","最新":"zuixin","排行":"paihang","榜单":"bangdan","最佳":"zuijia","原创":"yuanchuang","转发":"zhuanfa","点赞":"dianzan","评论":"pinglun","回复":"huifu","互动":"hudong","私信":"sixin","关注":"guanzhu","粉丝":"fensi","好友":"haoyou","群组":"qunzu","平台":"pingtai","渠道":"qudao","账号":"zhanghao","密码":"mima","登录":"denglu","注册":"zhuce","注销":"zhuxiao","退出":"tuichu","打开":"dakai","关闭":"guanbi","最小化":"zuixiaohua","最大化":"zuidahua","刷新":"shuaxin","加载":"jiazai","等待":"dengdai","成功":"chenggong","失败":"shibai","警告":"jinggao","错误":"cuowu","退出":"tuichu","取消":"quxiao","同意":"tongyi","拒绝":"jujue","确定":"queding","返回":"fanhui","下一步":"xiayibu","上一步":"shangyibu","完成":"wancheng","继续":"jixu","暂停":"zanting","重试":"chongci","跳过":"tiaoguo","部署":"bushu","上线":"shangxian","下线":"xiaxian","升级":"shengji","回滚":"huigun","测试":"ceshi","预发布":"yufabu","灰度":"huidu","A":"a","B":"b","C":"c","D":"d","E":"e","F":"f","G":"g","H":"h","I":"i","J":"j","K":"k","L":"l","M":"m","N":"n","O":"o","P":"p","Q":"q","R":"r","S":"s","T":"t","U":"u","V":"v","W":"w","X":"x","Y":"y","Z":"z"};

function toPinyin(name) {
  if (!name) return '';
  let out = '', i = 0;
  while (i < name.length) {
    const ch = name[i];
    if (/[a-zA-Z0-9\-_\s·]/.test(ch)) { out += ch.toLowerCase(); i++; continue; }
    let matched = false;
    for (let len = 4; len >= 1; len--) {
      const sub = name.substr(i, len);
      if (/^[\u4E00-\u9FFF]+$/.test(sub) && PY[sub]) { out += PY[sub]; i += len; matched = true; break; }
    }
    if (!matched) { out += ch; i++; }
  }
  return out.replace(/\s+/g, '').toLowerCase();
}
// 暴露给其它 dataviewjs 代码块（手机同步等）复用
try { window.__pmToPinyin = toPinyin; } catch (_) {}

// ---- 同步工具函数 ----
function getEscapedRegex(s) { return s.replace(/[.*+?^${}()|[\]\\]/g, '\\$&'); }

// 解析某行是否包含某个 [[link]] 引用了某个 card 文件
function lineContainsCardRef(line, basename, cardDir) {
  const m = line.match(/\[\[([^\]]+)\]\]/);
  if (!m) return false;
  const inner = m[1].split('|')[0].split('#')[0].trim();
  // 匹配多种 wiki link 写法：
  const f1 = inner.toLowerCase() === basename.toLowerCase() + '.md';
  const f2 = inner.toLowerCase() === basename.toLowerCase();
  const f3 = inner.toLowerCase().endsWith('/' + basename.toLowerCase() + '.md');
  const f4 = inner.toLowerCase().endsWith('/' + basename.toLowerCase());
  const cardDirLower = cardDir.toLowerCase();
  const f5 = inner.toLowerCase().startsWith(cardDirLower + '/') &&
             (inner.toLowerCase() === cardDirLower + '/' + basename.toLowerCase() ||
              inner.toLowerCase() === cardDirLower + '/' + basename.toLowerCase() + '.md');
  return f1 || f2 || f3 || f4 || f5;
}

// ---- 状态行 ----
const statusDiv = dv.el('div', '', { cls: 'pm-tools-status' });
statusDiv.style.cssText = 'padding:10px;margin-bottom:12px;border:1px solid var(--background-modifier-border);border-radius:6px;background:var(--background-secondary);font-family:var(--font-monospace);font-size:13px;';
statusDiv.textContent = '📡 同步状态：监听器' + (window.__pmSyncRegistered ? '已注册 ✅' : '正在注册…');

dv.el('h3', '⚡ 一键操作');
const toolbar = dv.el('div', '', { cls: 'pm-tools-toolbar' });
toolbar.style.cssText = 'display:flex;flex-wrap:wrap;gap:8px;margin-bottom:12px;';

// ---- 按钮 1: 一键生成所有缺失卡片 ----
const btnGen = dv.el('button', '⚡ 一键生成所有缺失卡片');
btnGen.style.cssText = 'background:var(--interactive-accent);color:var(--text-on-accent);border:none;border-radius:6px;padding:8px 14px;cursor:pointer;font-weight:bold;';
btnGen.onclick = async () => {
  btnGen.disabled = true;
  btnGen.textContent = '⏳ 扫描 board…';
  try {
    const boardFile = app.vault.getAbstractFileByPath(BOARD_PATH);
    if (!boardFile) { btnGen.textContent = '❌ 找不到 board'; return; }
    const tplFile = app.vault.getAbstractFileByPath(TEMPLATE_PATH);
    if (!tplFile) { btnGen.textContent = '❌ 找不到模板'; return; }
    const boardContent = await app.vault.read(boardFile);
    const tplContent = await app.vault.read(tplFile);

    const ymd = (() => { const d = new Date(); return d.getFullYear()+'-'+String(d.getMonth()+1).padStart(2,'0')+'-'+String(d.getDate()).padStart(2,'0'); })();

    let made = 0, skipped = 0, failed = 0;
    const lines = boardContent.split('\n');
    for (const line of lines) {
      const m = line.match(/\[\[([^\]]+)\]\]/);
      if (!m) continue;
      const linkText = m[1].split('|')[0].split('#')[0].trim();
      if (!linkText) continue;
      let targetPath = linkText.endsWith('.md') ? linkText : linkText + '.md';
      if (!targetPath.includes('/')) targetPath = CARD_DIR + '/' + targetPath;
      const existing = app.vault.getAbstractFileByPath(targetPath);
      if (existing) { skipped++; continue; }
      const title = targetPath.split('/').pop().replace(/\.md$/, '');
      const pinyin = toPinyin(title);
      const expanded = tplContent
        .replace(/\{\{title\}\}/g, title)
        .replace(/\{\{title_pinyin\}\}/g, pinyin)
        .replace(/\{\{date\}\}/g, ymd);
      try {
        await app.vault.create(targetPath, expanded);
        console.log('[PM-CM] CREATE ' + targetPath + ' pinyin=' + pinyin);
        made++;
      } catch (e) { console.error('[PM-CM] FAIL ' + targetPath, e); failed++; }
    }
    btnGen.textContent = `✅ 完成：新建 ${made}，已存在 ${skipped}` + (failed?`，失败 ${failed}`:'');
    dv.refresh();
  } catch (e) {
    console.error('[PM-CM] ERR', e);
    btnGen.textContent = '❌ 出错：' + e.message;
    btnGen.disabled = false;
  }
};
toolbar.appendChild(btnGen);

// ---- 按钮 2: 立即同步双向 ----
const btnSync = dv.el('button', '🔄 立即同步双向');
btnSync.style.cssText = 'background:var(--background-modifier-hover);color:var(--text-normal);border:1px solid var(--background-modifier-border);border-radius:6px;padding:8px 14px;cursor:pointer;';
btnSync.onclick = async () => {
  btnSync.disabled = true;
  btnSync.textContent = '⏳ 同步中…';
  try {
    const boardFile = app.vault.getAbstractFileByPath(BOARD_PATH);
    if (!boardFile) { btnSync.textContent = '❌ 找不到 board'; return; }
    const boardContent = await app.vault.read(boardFile);

    // === 正向同步：board 中 [[link]] 如果对应文件不存在，删除该行 ===
    const lines = boardContent.split('\n');
    const kept = [];
    let removedForward = 0;
    for (const line of lines) {
      const m = line.match(/\[\[([^\]]+)\]\]/);
      if (!m) { kept.push(line); continue; }
      const linkText = m[1].split('|')[0].split('#')[0].trim();
      let f = null;
      const tryPaths = [];
      const withMd = linkText.endsWith('.md') ? linkText : linkText + '.md';
      tryPaths.push(withMd);
      if (!linkText.includes('/')) tryPaths.push(CARD_DIR + '/' + withMd);
      // 替换 /Cards/ 为 cards dir 也尝试
      const cardIdx = linkText.toLowerCase().lastIndexOf('/cards/');
      if (cardIdx >= 0) {
        const root = linkText.substring(0, cardIdx);
        const base = linkText.substring(cardIdx + '/cards/'.length).split('/').pop();
        tryPaths.push(root + '/Cards/' + base);
      }
      for (const p of tryPaths) {
        f = app.vault.getAbstractFileByPath(p);
        if (f) break;
      }
      if (!f) {
        // fallback: Obsidian's metadataCache link resolution
        const resolved = app.metadataCache.getFirstLinkpathDest(linkText, boardFile.path);
        if (resolved) f = resolved;
      }
      if (f) {
        kept.push(line);
      } else {
        removedForward++;
        console.log('[PM-SYNC-FWD] removed orphan link for:', linkText);
      }
    }
    if (removedForward > 0) {
      await app.vault.modify(boardFile, kept.join('\n'));
      new Notice(`[PM-SYNC] 从 Main Board 移除 ${removedForward} 个孤立链接`);
    }

    // === 反向同步扫描：检查 board 中每个 wiki link 对应的文件是否还在；不在则也是上面 removedForward 已处理 ===
    // 反向 sync 的 listener 在文件删除时实时处理，本按钮的主要工作是 forward。
    btnSync.textContent = `✅ 完成：移除 ${removedForward} 个孤立链接`;
    dv.refresh();
  } catch (e) {
    console.error('[PM-SYNC] ERR', e);
    btnSync.textContent = '❌ 出错：' + e.message;
    btnSync.disabled = false;
  }
};
toolbar.appendChild(btnSync);

// ---- 按钮 3: 重建损坏卡片 ----
const btnRebuild = dv.el('button', '🔧 一键重建所有损坏卡片');
btnRebuild.style.cssText = 'background:var(--background-modifier-hover);color:var(--text-normal);border:1px solid var(--background-modifier-border);border-radius:6px;padding:8px 14px;cursor:pointer;';
btnRebuild.onclick = async () => {
  btnRebuild.disabled = true;
  btnRebuild.textContent = '⏳ 重建中…';
  try {
    const boardFile = app.vault.getAbstractFileByPath(BOARD_PATH);
    const tplFile = app.vault.getAbstractFileByPath(TEMPLATE_PATH);
    if (!boardFile || !tplFile) { btnRebuild.textContent = '❌ 找不到文件'; return; }
    const boardContent = await app.vault.read(boardFile);
    const tplContent = await app.vault.read(tplFile);
    const ymd = (() => { const d = new Date(); return d.getFullYear()+'-'+String(d.getMonth()+1).padStart(2,'0')+'-'+String(d.getDate()).padStart(2,'0'); })();
    let rebuilt = 0, skipped = 0;
    const lines = boardContent.split('\n');
    for (const line of lines) {
      const m = line.match(/\[\[([^\]]+)\]\]/);
      if (!m) continue;
      const linkText = m[1].split('|')[0].split('#')[0].trim();
      let targetPath = linkText.endsWith('.md') ? linkText : linkText + '.md';
      if (!targetPath.includes('/')) targetPath = CARD_DIR + '/' + targetPath;
      const f = app.vault.getAbstractFileByPath(targetPath);
      if (!f) { skipped++; continue; }
      const ct = await app.vault.read(f);
      if (ct.length >= 200) { skipped++; continue; }
      const title = targetPath.split('/').pop().replace(/\.md$/, '');
      const pinyin = toPinyin(title);
      const expanded = tplContent
        .replace(/\{\{title\}\}/g, title)
        .replace(/\{\{title_pinyin\}\}/g, pinyin)
        .replace(/\{\{date\}\}/g, ymd);
      try {
        await app.vault.modify(f, expanded);
        console.log('[PM-CM] REBUILD ' + targetPath + ' pinyin=' + pinyin);
        rebuilt++;
      } catch (e) { console.error('[PM-CM] FAIL ' + targetPath, e); }
    }
    btnRebuild.textContent = `✅ 完成：重建 ${rebuilt}，跳过 ${skipped}`;
    dv.refresh();
  } catch (e) {
    console.error('[PM-CM] ERR', e);
    btnRebuild.textContent = '❌ 出错：' + e.message;
    btnRebuild.disabled = false;
  }
};
toolbar.appendChild(btnRebuild);

// ---- 状态 / 日志 ----
const log = dv.el('pre', '', { cls: 'pm-tools-log' });
log.style.cssText = 'background:var(--background-primary-alt);padding:8px;border-radius:6px;font-size:12px;max-height:160px;overflow:auto;color:var(--text-muted);margin-top:8px;';
log.textContent = '[PM-SYNC] PM Tools 已加载。';
const origLog = console.log;
const origErr = console.error;
const origWarn = console.warn;
function appendLog(level, args) {
  try {
    const ts = new Date().toTimeString().slice(0,8);
    const text = args.map(a => (typeof a === 'string' ? a : JSON.stringify(a))).join(' ');
    if (text.includes('PM-')) {
      log.textContent += `\n${ts} [${level}] ${text.slice(0, 200)}`;
    }
  } catch (_) {}
}
console.log = function(...args){ appendLog('LOG', args); origLog.apply(console, args); };
console.warn = function(...args){ appendLog('WARN', args); origWarn.apply(console, args); };
console.error = function(...args){ appendLog('ERR', args); origErr.apply(console, args); };

// ---- 反向同步监听器（每次只注册一次） ----
if (!window.__pmSyncRegistered) {
  window.__pmSyncRegistered = true;

  // 反向：card 文件被删除 → 把 Main Board 中对应行去掉
  const onVaultDelete = async (file) => {
    try {
      if (!file || typeof file.path !== 'string') return;
      // 只关心 Cards 目录下的文件
      if (!file.path.includes('/Cards/')) return;
      const basename = file.basename;
      const boardFile = app.vault.getAbstractFileByPath(BOARD_PATH);
      if (!boardFile) return;
      const boardContent = await app.vault.read(boardFile);
      const lines = boardContent.split('\n');
      const kept = [];
      let removed = 0;
      for (const line of lines) {
        if (lineContainsCardRef(line, basename, CARD_DIR)) {
          removed++;
          console.log('[PM-SYNC-REV] detected deleted card "' + basename + '", removing board link line');
        } else {
          kept.push(line);
        }
      }
      if (removed > 0) {
        await app.vault.modify(boardFile, kept.join('\n'));
        new Notice(`[PM-SYNC] 已从 Main Board 移除「${basename}」`);
      }
    } catch (e) {
      console.warn('[PM-SYNC-REV] handler err', e);
    }
  };

  // 正向：Main Board 修改 → 检查新增的 link 是否需要补卡（辅助）
  const onBoardModify = async (file) => {
    try {
      if (!file || file.path !== BOARD_PATH) return;
      // 不主动生成新卡（避免误触）。如要手动扫描请按"⚡ 生成"按钮。
    } catch (e) {}
  };

  app.vault.on('delete', onVaultDelete);
  app.vault.on('modify', onBoardModify);

  // ---- 项目上下文跟踪：监听 file-open，记录最近打开的 card 文件名/ID
  //     Log Time 视图会读取 window.__pmLastProject 自动预选下拉。
  if (!window.__pmContextTracker) {
    window.__pmContextTracker = true;
    const ctxHandler = (file) => {
      try {
        if (!file) return;
        const p = String(file.path || '');
        // 卡片文件都位于 Cards/ 子目录
        const cardIdx = Math.max(p.lastIndexOf('/Cards/'), p.lastIndexOf('\\Cards\\'));
        if (cardIdx === -1) return;
        const basename = file.basename;
        const fc = app.metadataCache.getFileCache(file);
        const id = (fc && fc.frontmatter && fc.frontmatter.id) || basename;
        window.__pmLastProject = basename;
        window.__pmLastProjectId = id;
        console.log('[PM-CTX] updated last project =', basename, '/ id =', id);
      } catch (e) { console.warn('[PM-CTX] handler err', e); }
    };
    app.workspace.on('file-open', ctxHandler);
    // 也对当前已经激活的文件立即执行一次（用户可能先开本文件，trace 不到历史）
    const cur = app.workspace.getActiveFile();
    if (cur) ctxHandler(cur);
    console.log('[PM-CTX] context tracker registered');
  }
  statusDiv.textContent = '📡 监听器已注册 ✅  (删除同步 + 项目上下文跟踪)';
  console.log('[PM-SYNC] listeners registered (delete + modify + file-open)');
}
```

---

## 📱 手机同步 / Mobile

手机端**不需要插件**：只编辑 `Views/📱 手机速记.md`（纯 Markdown），同步回电脑后点下面的按钮处理。
也可以直接在 Main Board 的 Icebox 里加纯文字条目，再用「⚡ Icebox 未链接条目 → 卡片」把它们升级成卡片。

```dataviewjs
// =============================================================
// PM Tools v2 — 手机同步：速记 → 卡片 / 日志，刷新手机速览
// =============================================================
// ==== PM2 LOGIC START ====
const m2_BOARD          = "Boards/Main Board.md";
const m2_CARD_DIR       = "Cards";
const m2_TEMPLATE       = "Templates/card.md";
const m2_DAILY_TPL      = "Templates/daily.md";
const m2_CAPTURE        = "Views/📱 手机速记.md";
const m2_MOBILE_INDEX   = "Views/📱 项目速览.md";
const m2_DESC_HOLDER    = "用一句话说明这个项目要做什么。";

function m2_pad(n) { return String(n).padStart(2, '0'); }
function m2_ymd(d) { return d.getFullYear() + '-' + m2_pad(d.getMonth() + 1) + '-' + m2_pad(d.getDate()); }
function m2_stamp(d) { return m2_ymd(d) + ' ' + m2_pad(d.getHours()) + ':' + m2_pad(d.getMinutes()); }
function m2_normTime(s) { const t = String(s).match(/^(\d{1,2}):(\d{2})$/); return t ? m2_pad(+t[1]) + ':' + t[2] : String(s); }
function m2_notice(msg) { try { if (typeof Notice === 'function') new Notice(msg); } catch (_) {} }
function m2_sanitizeName(n) { return String(n || '').replace(/[\\/:*?"<>|]/g, ' ').replace(/\s+/g, ' ').trim(); }

// 拼音：优先复用第一段代码块里挂到 window 的 toPinyin
function m2_toPinyin(name) {
  try {
    if (typeof window !== 'undefined' && typeof window.__pmToPinyin === 'function') return window.__pmToPinyin(name);
  } catch (_) {}
  return String(name || '').replace(/[^\w\u4e00-\u9fff\-. ]/g, '').replace(/\s+/g, '').toLowerCase();
}

// ---- 解析 Main Board 的泳道 ----
async function m2_readBoardLanes(app) {
  const bf = app.vault.getAbstractFileByPath(m2_BOARD);
  if (!bf) return [];
  const content = await app.vault.read(bf);
  const lines = String(content).split('\n');
  const lanes = [];
  let cur = null;
  for (const ln of lines) {
    if (/^%%\s*kanban:settings/.test(ln)) break;
    const hm = ln.match(/^##\s+(.+?)\s*$/);
    if (hm) { cur = { name: hm[1].trim(), items: [] }; lanes.push(cur); continue; }
    if (!cur) continue;
    const im = ln.match(/^\s*[-*]\s*\[[ xX]\]\s*(.*)$/);
    if (im) { const t = im[1].trim(); if (t) cur.items.push(t); }
  }
  return lanes;
}

// ---- 从卡片正文抽取 描述 / 详细文档 / 待办数 ----
function m2_extractDesc(content) {
  const m = String(content).match(/###\s*描述\s*\/\s*Description\s*\r?\n+\s*>\s*(.+?)\s*(?:\r?\n|$)/);
  if (!m) return '';
  const d = m[1].trim();
  return d === m2_DESC_HOLDER ? '' : d;
}
function m2_extractDocLink(content) {
  const m = String(content).match(/📄[ \t]*详细文档[ \t]*[:：][ \t]*(.*)/);
  if (!m) return null;
  const raw = m[1].trim();
  if (!raw) return null;
  // 1) vault 内：[[path|alias]]
  const lm = raw.match(/\[\[([^\]|#]+?)(?:\|([^\]]+))?\]\]/);
  if (lm) return { target: lm[1].trim(), alias: (lm[2] || lm[1].split('/').pop() || lm[1]).trim(), raw, external: false };
  // 2) vault 外：[text](<file:///...>)
  const mm = raw.match(/\[([^\]]+)\]\((?:<)?(file:\/\/\/[^>)]+)(?:>)?\)/);
  if (mm) {
    let p = mm[2];
    try { p = decodeURIComponent(p.replace(/^file:\/\/\//, '')); } catch (_) {}
    return { target: '', alias: mm[1].trim(), raw, external: true, url: mm[2], path: p };
  }
  return { target: '', alias: raw, raw, external: false };
}
function m2_countPending(content) {
  // 逐行判断，避免 \s* 跨行把别的行算进来
  let n = 0;
  for (const line of String(content).split(/\r?\n/)) {
    const m = line.match(/^[ \t]*[-*][ \t]*\[ \][ \t]*(.*)$/);
    if (m && m[1].trim()) n++;
  }
  return n;
}

// ---- 解析「手机速记」----
function m2_parseCapture(content) {
  const lines = String(content).split('\n');
  const ideas = [], logs = [];
  let mode = null;
  for (const ln of lines) {
    const hm = ln.match(/^##\s+(.*)$/);
    if (hm) {
      const h = hm[1];
      if (/💡|想法|idea/i.test(h)) mode = 'idea';
      else if (/⏱|日志|log/i.test(h)) mode = 'log';
      else mode = null;
      continue;
    }
    if (!mode) continue;
    const im = ln.match(/^\s*[-*]\s+(.*)$/);
    if (!im) continue;
    const v = im[1].trim();
    if (!v || v.startsWith('<!--')) continue;
    (mode === 'idea' ? ideas : logs).push(v);
  }
  return { ideas, logs };
}

// ---- 解析一行日志 ----
function m2_parseLogEntry(raw, today) {
  const src = String(raw || '').trim();
  let date = today;

  // 1) 日期（先于时间段解析，避免 20:00-22:00 的 - 被当成日期）
  let dateTok = null;
  let dm = src.match(/\d{4}-\d{1,2}-\d{1,2}/);
  if (dm) {
    dateTok = dm[0];
    const p = dm[0].split('-');
    date = p[0] + '-' + m2_pad(+p[1]) + '-' + m2_pad(+p[2]);
  } else {
    dm = src.match(/(?:^|[\s|])(\d{1,2})-(\d{1,2})(?=[\s|]|$)/);
    if (dm) { dateTok = dm[0].trim(); date = today.slice(0, 4) + '-' + m2_pad(+dm[1]) + '-' + m2_pad(+dm[2]); }
  }

  // 2) 时间段 HH:MM-HH:MM
  let start = '', end = '';
  const tr = src.match(/(\d{1,2}:\d{2})\s*[-~～—至到]\s*(\d{1,2}:\d{2})/);
  if (tr) { start = m2_normTime(tr[1]); end = m2_normTime(tr[2]); }

  // 3) 按 | 切段（保留位置，不丢空段）
  let work = src;
  if (dateTok) work = work.replace(dateTok, ' ');
  const segs = work.split('|').map(s => s.trim());
  let head = (segs[0] || '').replace(/\s+/g, ' ').trim();
  let mid = (segs[1] || '').replace(/\s+/g, ' ').trim();
  const note = segs.slice(2).join(' ').replace(/\s+/g, ' ').trim();

  // 4) 只有一段时，尝试把结尾的时长 / 时间段拆出来
  if (segs.length === 1) {
    const mm = head.match(/^(.*?)\s+((?:\d{1,2}:\d{2}\s*[-~～—至到]\s*\d{1,2}:\d{2})|\d+(?:\.\d+)?\s*(?:h|hr|hrs|hour|hours|小时|min|mins|分钟|m)?)\s*$/i);
    if (mm) { head = mm[1].trim(); mid = mm[2].trim(); }
  }

  // 5) 时长只从第 2 段解析，避免项目名里的数字（如 3d地形）被误判
  let hours = null;
  if (!start && mid) {
    const h = mid.match(/(\d+(?:\.\d+)?)\s*(h|hr|hrs|hour|hours|小时|min|mins|分钟|m)?/i);
    if (h) {
      let v = parseFloat(h[1]);
      const u = (h[2] || '').toLowerCase();
      if (u === 'min' || u === 'mins' || u === '分钟' || u === 'm') v = v / 60;
      if (isFinite(v) && v > 0) hours = Math.round(v * 100) / 100;
    }
  }
  return { project: m2_sanitizeName(head), date: date, note: note, start: start, end: end, hours: hours };
}

// ---- 生成日志行（与 Log Time 视图格式一致）----
function m2_buildJournalLine(entry, idMap) {
  const key = String(entry.project || '').toLowerCase();
  const id = (idMap && idMap.get(key)) || entry.project;
  const tail = entry.note ? ' ' + entry.note : '';
  let line;
  if (entry.start && entry.end) line = '- [x] ' + id + tail + ' [start:: ' + entry.start + '] [end:: ' + entry.end + '] ✅ ' + entry.date;
  else if (entry.hours !== null && entry.hours !== undefined) line = '- [x] ' + id + tail + ' [dur:: ' + entry.hours + '] ✅ ' + entry.date;
  else line = '- [x] ' + id + tail + ' ✅ ' + entry.date;
  return { id, line };
}

// ---- 写入 Journal ----
async function m2_appendJournal(app, dateStr, line) {
  const p = 'Journal/' + dateStr + '.md';
  const file = app.vault.getAbstractFileByPath(p);
  if (!file) {
    let body = '';
    const tpl = app.vault.getAbstractFileByPath(m2_DAILY_TPL);
    if (tpl) { try { body = await app.vault.read(tpl); } catch (_) {} }
    body = String(body).replace(/\s+$/, '');
    if (!body) body = '## Log';
    await app.vault.create(p, body + '\n' + line + '\n');
    return p;
  }
  await app.vault.process(file, (c) => {
    let body = String(c).replace(/\s+$/, '');
    if (!/\n## Log\b/m.test('\n' + body)) body = (body ? body + '\n\n' : '') + '## Log';
    return body + '\n' + line + '\n';
  });
  return p;
}

// ---- 卡片 id / 信息映射 ----
async function m2_buildCardIdMap(app) {
  const map = new Map();
  const files = app.vault.getMarkdownFiles().filter(f => f.path.startsWith(m2_CARD_DIR + '/'));
  const tokens = [];
  for (const f of files) {
    let fm = {};
    try { const fc = app.metadataCache.getFileCache(f); fm = (fc && fc.frontmatter) || {}; } catch (_) {}
    const id = fm.id || f.basename;
    map.set(String(f.basename).toLowerCase(), id);
    map.set(String(id).toLowerCase(), id);
    // 标题可能是 "Fitness / 健身" 这种复合写法，拆词建索引，方便手机端直接写中文名
    for (const t of [fm.title, f.basename]) {
      if (!t) continue;
      for (const tok of String(t).split(/[\/|·,，、\-–—\s]+/)) {
        if (tok) tokens.push([tok.toLowerCase(), id]);
      }
    }
  }
  for (const kv of tokens) if (!map.has(kv[0])) map.set(kv[0], kv[1]);
  return map;
}
async function m2_buildCardInfoMap(app) {
  const map = new Map();
  const files = app.vault.getMarkdownFiles().filter(f => f.path.startsWith(m2_CARD_DIR + '/'));
  for (const f of files) {
    try {
      const c = await app.vault.read(f);
      const info = { title: f.basename, desc: m2_extractDesc(c), doc: m2_extractDocLink(c), pending: m2_countPending(c) };
      map.set(f.path.replace(/\.md$/, ''), info);
      map.set(f.basename, info);
    } catch (_) {}
  }
  return map;
}

// ---- 建卡片 + 写进 Icebox ----
async function m2_ensureCard(app, rawName) {
  const name = m2_sanitizeName(rawName);
  const targetPath = m2_CARD_DIR + '/' + name + '.md';
  if (app.vault.getAbstractFileByPath(targetPath)) return { name, path: targetPath, created: false };
  const tplFile = app.vault.getAbstractFileByPath(m2_TEMPLATE);
  if (!tplFile) return { name, path: targetPath, created: false, error: '模板缺失' };
  const tpl = await app.vault.read(tplFile);
  const content = String(tpl)
    .replace(/\{\{title\}\}/g, name)
    .replace(/\{\{title_pinyin\}\}/g, m2_toPinyin(name))
    .replace(/\{\{date\}\}/g, m2_ymd(new Date()));
  await app.vault.create(targetPath, content);
  return { name, path: targetPath, created: true };
}
async function m2_upsertIcebox(app, targetPathNoExt, name) {
  const bf = app.vault.getAbstractFileByPath(m2_BOARD);
  if (!bf) return 'no-board';
  const content = await app.vault.read(bf);
  const lines = String(content).split('\n');
  if (lines.some(l => l.includes(targetPathNoExt))) return 'exists';
  const hIdx = lines.findIndex(l => /^##\s*Icebox\s*$/i.test(l));
  if (hIdx === -1) return 'no-lane';
  const link = '[[' + targetPathNoExt + '|' + name + ']]';
  let end = lines.length;
  for (let i = hIdx + 1; i < lines.length; i++) {
    if (/^##\s/.test(lines[i]) || /^%%/.test(lines[i])) { end = i; break; }
    const im = lines[i].match(/^(\s*[-*]\s*\[[ xX]\]\s*)(.*)$/);
    if (im && !im[2].includes('[[') && im[2].trim() === name) {
      lines[i] = im[1] + link;
      await app.vault.modify(bf, lines.join('\n'));
      return 'replaced';
    }
  }
  let at = end;
  while (at - 1 > hIdx && lines[at - 1].trim() === '') at--;
  lines.splice(at, 0, link);
  await app.vault.modify(bf, lines.join('\n'));
  return 'appended';
}

// ---- 主流程：处理手机速记 ----
async function m2_processCapture(app) {
  const rpt = { ideas: [], logs: [], errors: [] };
  const cf = app.vault.getAbstractFileByPath(m2_CAPTURE);
  if (!cf) { rpt.errors.push('找不到 ' + m2_CAPTURE); return rpt; }
  const content = await app.vault.read(cf);
  const parsed = m2_parseCapture(content);
  const idMap = await m2_buildCardIdMap(app);
  const today = m2_ymd(new Date());

  for (const rawName of parsed.ideas) {
    try {
      const made = await m2_ensureCard(app, rawName);
      const where = await m2_upsertIcebox(app, made.path.replace(/\.md$/, ''), made.name);
      rpt.ideas.push({ name: made.name, created: made.created, icebox: where });
    } catch (e) { rpt.errors.push('想法『' + rawName + '』: ' + (e && e.message)); }
  }
  for (const raw of parsed.logs) {
    try {
      const entry = m2_parseLogEntry(raw, today);
      if (!entry.project) { rpt.errors.push('日志缺项目名: ' + raw); continue; }
      const built = m2_buildJournalLine(entry, idMap);
      const p = await m2_appendJournal(app, entry.date, built.line);
      rpt.logs.push({ raw: raw, id: built.id, date: entry.date, line: built.line, path: p });
    } catch (e) { rpt.errors.push('日志『' + raw + '』: ' + (e && e.message)); }
  }
  return rpt;
}

// ---- 把 Icebox 里未链接的纯文字条目升级成卡片 ----
async function m2_promoteAllIcebox(app) {
  const rpt = { made: [], errors: [] };
  const lanes = await m2_readBoardLanes(app);
  const ice = lanes.find(l => /^icebox$/i.test(l.name.trim()));
  if (!ice) { rpt.errors.push('未找到 Icebox 泳道'); return rpt; }
  const plain = ice.items.filter(t => !t.includes('[['));
  for (const rawName of plain) {
    try {
      const made = await m2_ensureCard(app, rawName);
      const where = await m2_upsertIcebox(app, made.path.replace(/\.md$/, ''), made.name);
      rpt.made.push({ name: made.name, created: made.created, icebox: where });
    } catch (e) { rpt.errors.push('『' + rawName + '』: ' + (e && e.message)); }
  }
  return rpt;
}

// ---- 生成「手机速览」（纯 Markdown，手机端免插件可读）----
async function m2_buildMobileIndex(app) {
  const lanes = await m2_readBoardLanes(app);
  const info = await m2_buildCardInfoMap(app);
  const out = [];
  out.push('# 📱 项目速览 / Mobile Index');
  out.push('');
  out.push('> 自动生成，请勿手动编辑。最后更新：' + m2_stamp(new Date()));
  out.push('> 重新生成：电脑端打开 `Boards/PM Tools` → 点「📱 刷新手机速览」。');
  out.push('');
  out.push('## ⚡ 快捷入口');
  out.push('');
  out.push('- [[Views/📱 手机速记|📱 手机速记（加想法 / 记日志）]]');
  out.push('- [[Boards/Main Board|🚩 Main Board（完整看板）]]');
  out.push('- [[Views/Log Time|⏱ Log Time（电脑端记日志）]]');
  out.push('');
  for (const lane of lanes) {
    out.push('## ' + lane.name);
    out.push('');
    if (!lane.items.length) { out.push('*（空 / empty）*'); out.push(''); continue; }
    for (const it of lane.items) {
      const lm = it.match(/^\[\[([^\]|#]+?)(?:\|([^\]]+))?\]\](.*)$/);
      if (lm) {
        const target = lm[1].trim();
        const alias = (lm[2] || target.split('/').pop() || target).trim();
        const rest = (lm[3] || '').trim();
        const k = target.replace(/\.md$/, '');
        const ci = info.get(k) || info.get(k.split('/').pop());
        const bits = [];
        if (ci && ci.desc) bits.push(ci.desc);
        if (ci && ci.pending > 0) bits.push('⏳ ' + ci.pending);
        if (rest) bits.push(rest);
        out.push('- [[' + target + '|' + alias + ']]' + (bits.length ? ' — ' + bits.join(' · ') : ''));
      } else {
        out.push('- ' + it + '  *(未建卡片)*');
      }
    }
    out.push('');
  }
  return out.join('\n');
}
async function m2_refreshMobileIndex(app) {
  const md = await m2_buildMobileIndex(app);
  const f = app.vault.getAbstractFileByPath(m2_MOBILE_INDEX);
  if (f) await app.vault.modify(f, md);
  else await app.vault.create(m2_MOBILE_INDEX, md);
  return md;
}
// ==== PM2 LOGIC END ====

// ==== PM2 UI ====
dv.el('h3', '📱 手机同步 / Mobile');
const m2_hint = dv.el('div', '手机端只改 Views/📱 手机速记.md（纯 Markdown，无需插件）。回到电脑点下面的按钮处理即可。');
m2_hint.style.cssText = 'font-size:12px;color:var(--text-muted);margin-bottom:8px;';

const m2_bar = dv.el('div', '');
m2_bar.style.cssText = 'display:flex;flex-wrap:wrap;gap:8px;margin-bottom:8px;';
function m2_mkBtn(label, primary) {
  const b = dv.el('button', label);
  b.style.cssText = primary
    ? 'background:var(--interactive-accent);color:var(--text-on-accent);border:none;border-radius:6px;padding:8px 14px;cursor:pointer;font-weight:bold;'
    : 'background:var(--background-modifier-hover);color:var(--text-normal);border:1px solid var(--background-modifier-border);border-radius:6px;padding:8px 14px;cursor:pointer;';
  m2_bar.appendChild(b);
  return b;
}

const m2_log = dv.el('pre', '');
m2_log.style.cssText = 'background:var(--background-primary-alt);padding:8px;border-radius:6px;font-size:12px;max-height:200px;overflow:auto;color:var(--text-muted);';
m2_log.textContent = '[PM-CAP] 就绪。';
function m2_append(s) { m2_log.textContent += '\n' + s; m2_log.scrollTop = m2_log.scrollHeight; }

const m2_bCap = m2_mkBtn('📥 处理手机速记', true);
m2_bCap.onclick = async () => {
  m2_bCap.disabled = true; m2_bCap.textContent = '⏳ 处理中…';
  try {
    const r = await m2_processCapture(app);
    m2_append('[PM-CAP] 想法 ' + r.ideas.length + ' 条 / 日志 ' + r.logs.length + ' 条 / 错误 ' + r.errors.length);
    r.ideas.forEach(i => m2_append('  💡 ' + i.name + ' → 卡片' + (i.created ? '新建' : '已存在') + '（Icebox: ' + i.icebox + '）'));
    r.logs.forEach(l => m2_append('  ⏱ ' + l.line + '  → ' + l.path));
    r.errors.forEach(e => m2_append('  ❌ ' + e));
    m2_notice('[PM-CAP] 处理完成：想法 ' + r.ideas.length + ' / 日志 ' + r.logs.length);
    if (r.ideas.length || r.logs.length) dv.refresh();
  } catch (e) { m2_append('[PM-CAP] ERR ' + e.message); }
  m2_bCap.textContent = '📥 处理手机速记'; m2_bCap.disabled = false;
};

const m2_bPromote = m2_mkBtn('⚡ Icebox 未链接条目 → 卡片');
m2_bPromote.onclick = async () => {
  m2_bPromote.disabled = true; m2_bPromote.textContent = '⏳ 处理中…';
  try {
    const r = await m2_promoteAllIcebox(app);
    m2_append('[PM-CAP] Icebox 升级 ' + r.made.length + ' 条 / 错误 ' + r.errors.length);
    r.made.forEach(i => m2_append('  🆕 ' + i.name + ' → 卡片' + (i.created ? '新建' : '已存在') + '（Icebox: ' + i.icebox + '）'));
    r.errors.forEach(e => m2_append('  ❌ ' + e));
    m2_notice('[PM-CAP] Icebox 升级 ' + r.made.length + ' 条');
    if (r.made.length) dv.refresh();
  } catch (e) { m2_append('[PM-CAP] ERR ' + e.message); }
  m2_bPromote.textContent = '⚡ Icebox 未链接条目 → 卡片'; m2_bPromote.disabled = false;
};

const m2_bIdx = m2_mkBtn('📱 刷新手机速览');
m2_bIdx.onclick = async () => {
  m2_bIdx.disabled = true; m2_bIdx.textContent = '⏳ 生成中…';
  try {
    await m2_refreshMobileIndex(app);
    m2_append('[PM-IDX] 已刷新 ' + m2_MOBILE_INDEX);
    m2_notice('[PM-IDX] 手机速览已刷新');
  } catch (e) { m2_append('[PM-IDX] ERR ' + e.message); }
  m2_bIdx.textContent = '📱 刷新手机速览'; m2_bIdx.disabled = false;
};
```

## 📋 全项目待办汇总 / All Pending

```dataviewjs
// 汇总所有卡片「### 待办 / Pending」里未完成的任务
const rows = [];
for (const p of dv.pages('"Cards"')) {
  const tasks = (p.file.tasks || []).filter(t => !t.completed && String(t.text || '').trim());
  for (const t of tasks) rows.push([p.file.link, String(t.text).trim()]);
}
if (!rows.length) {
  dv.paragraph('暂无待办 / No pending tasks.');
} else {
  dv.table(['项目 / Project', '待办 / Task'], rows);
}
```

---

## 用法

1. **首次使用**：打开本文件一次（命令面板 `Ctrl+O` → `Boards/PM Tools`）
2. **生成卡片**：在 Main Board 加新项目后，点 `⚡ 一键生成所有缺失卡片`
3. **删卡片 2 种方式**：
   - 在 Main Board 卡片右下角菜单点 `Archive` 或 `Delete card` → 已绑定 `_pmSyncDelCard`（main.js 补丁）→ 自动删除对应 `.md` 文件
   - 在文件管理器直接删 `Cards/*.md` → 本文件监听器触发 → 自动移除 Main Board 中的链接
4. **手动同步**：点 `🔄 立即同步双向`，清理 Main Board 中的孤立链接
5. **手机端工作流**（详见下方「📱 手机同步」）：
   - 手机 → 编辑 `Views/📱 手机速记.md`（纯 Markdown，无需插件），加入想法 / 日志 → 同步
   - 电脑 → 本文件点 `📥 处理手机速记` → 自动建卡片、加进 Icebox、写 Journal 日志
   - 也可以在 Main Board 的 Icebox 里直接写纯文字条目，再用 `⚡ Icebox 未链接条目 → 卡片` 升级
   - 点 `📱 刷新手机速览` 重新生成 `Views/📱 项目速览.md`（手机端看板概览）
6. **项目描述 / 待办**：每张卡片正文里有 `### 描述 / Description` 与 `### 待办 / Pending`；
   有独立长文档的项目，把链接写在 `📄 详细文档：` 后面即可一键跳转（例：`Cards/am-mix.md` →
   `AI music/ai音乐mv`）。新建卡片会自动带上这两个小节（模板 `Templates/card.md`）。
   汇总视图见 `Views/Projects.md`（描述 · 文档跳转 · 待办数）和本页「📋 全项目待办汇总」。

## 不影响 Kanban

- DataviewJS 独立于 Kanban 渲染
- 监听器在 Obsidian 内核，比 Kanban main.js 更稳定
- 任何插件更新都不会丢失本工具的配置

---

*实现版本: PM Tools v1 / 2026-09-12*
