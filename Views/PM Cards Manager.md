# PM Cards Manager / 项目卡片管理
---

```dataviewjs
// ============================================================
// PM Cards Manager — 独立于 Kanban 的卡片模板生成工具
// ============================================================
const BOARD_PATH = "Boards/Main Board.md";
const CARD_DIR   = "Cards";
const TEMPLATE_PATH = "Templates/card.md";

// 内联常用汉字 → 拼音字典（500+ 字，覆盖绝大多数项目名）
const PY = {"了":"le","我":"wo","你":"ni","他":"ta","她":"ta","它":"ta","们":"men","的":"de","是":"shi","在":"zai","有":"you","和":"he","不":"bu","一":"yi","也":"ye","都":"dou","就":"jiu","说":"shuo","要":"yao","看":"kan","能":"neng","到":"dao","说":"shuo","去":"qu","来":"lai","做":"zuo","给":"gei","把":"ba","让":"rang","着":"zhe","过":"guo","下":"xia","上":"shang","这":"zhe","那":"na","里":"li","还":"hai","没":"mei","很":"hen","多":"duo","少":"shao","大":"da","小":"xiao","好":"hao","新":"xin","旧":"jiu","高":"gao","低":"di","长":"chang","短":"duan","先":"xian","后":"hou","前":"qian","天":"tian","年":"nian","月":"yue","日":"ri","时":"shi","分":"fen","点":"dian","现在":"xianzai","今天":"jintian","明天":"mingtian","昨天":"zuotian","工作":"gongzuo","生活":"shenghuo","项目":"xiangmu","测试":"ceshi","音乐":"yinyue","视频":"shipin","解读":"jiedu","顶刊":"dingkan","混音":"hunyin","音乐mv":"yinlemv","音乐mv":"yinlemv","交响":"jiaoxiang","交响曲":"jiaoxiangqu","诺兰":"nuolan","创作":"chuangzuo","写作":"xiezuo","设计":"sheji","开发":"kaifa","研究":"yanjiu","分析":"fenxi","管理":"guanli","计划":"jihua","报告":"baogao","笔记":"biji","日记":"riji","日志":"rizhi","模板":"muban","目录":"mulu","文件":"wenjian","文档":"wendang","卡片":"kapian","看板":"kanban","项目库":"xiangmuku","笔记库":"bijiku","笔记系统":"bijixitong","音乐mv":"yinlemv","专辑":"zhuanji","制作":"zhizuo","录制":"luzhi","剪辑":"jianji","发布":"fabu","脚本":"jiaoben","歌词":"geci","作曲":"zuoqu","编曲":"bianqu","演唱":"yanchang","歌手":"geshou","歌名":"geming","节奏":"jiezou","旋律":"xuanlu","和声":"hesheng","混响":"hunxiang","效果":"xiaoguo","风格":"fengge","氛围":"fenwei","情绪":"qingxu","情感":"qinggan","感情":"ganqing","感觉":"ganjue","画面":"huamian","色彩":"secai","光线":"guangxian","镜头":"jingtou","场景":"changjing","故事":"gushi","剧情":"juqing","情节":"qingjie","人物":"renwu","角色":"juese","主角":"zhujue","配角":"peijue","电影":"dianying","电视剧":"dianshiju","动漫":"dongman","动画":"donghua","漫画":"manhua","小说":"xiaoshuo","散文":"sanwen","诗歌":"shige","文学":"wenxue","艺术":"yishu","科技":"keji","科学":"kexue","技术":"jishu","产品":"chanpin","功能":"gongneng","特点":"tedian","优势":"youshi","劣势":"lieshi","需求":"xuqiu","解决方案":"jiejuefangan","应用":"yingyong","平台":"pingtai","系统":"xitong","架构":"jiagou","模块":"mokuai","组件":"zujian","接口":"jiekou","数据":"shuju","数据库":"shujuku","用户":"yonghu","权限":"quanxian","登录":"denglu","注册":"zhuce","密码":"mima","账号":"zhanghao","主页":"zhuye","内容":"neirong","页面":"yemian","链接":"lianjie","图片":"tupian","视频文件":"shipinwenjian","音频":"yinpin","格式":"geshi","压缩":"yasuo","解压":"jieya","上传":"shangchuan","下载":"xiazhai","同步":"tongbu","备份":"beifen","恢复":"huifu","配置":"peizhi","设置":"shezhi","选项":"xuanxiang","参数":"cansh","状态":"zhuangtai","信息":"xinxi","提示":"tishi","错误":"cuowu","警告":"jinggao","成功":"chenggong","失败":"shibai","完成":"wancheng","开始":"kaishi","结束":"jieshu","暂停":"zanting","继续":"jixu","取消":"quxiao","确认":"queren","返回":"fanhui","下一步":"xiayibu","上一步":"shangyibu","提交":"tijiao","保存":"baocun","删除":"shanchu","修改":"xiugai","编辑":"bianji","新建":"xinjian","打开":"dakai","关闭":"guanbi","退出":"tuichu","导入":"daoru","导出":"daochu","搜索":"sousuo","筛选":"shaixuan","排序":"paixu","分类":"fenlei","标签":"biaoqian","归档":"guidang","收藏":"shoucang","关注":"guanzhu","点赞":"dianzan","评论":"pinglun","分享":"fenxiang","转发":"zhuanfa","回复":"huifu","艾特":"aite","消息":"xiaoxi","通知":"tongzhi","公告":"gonggao","新闻":"xinwen","动态":"dongtai","日志":"rizhi","周报":"zhoubao","月报":"yuebao","年报":"nianbao","总结":"zongjie","复盘":"fupan","反思":"fansi","笔记":"biji","摘抄":"zhaiqiao","引用":"yinyong","参考资料":"cankaoziliao","原文":"yuanwen","翻译":"fanyi","校对":"jiaodui","校对稿":"jiaoduigao","终稿":"zhonggao","草稿":"caogao","初稿":"chugao","样本":"yangben","模板":"muban","例子":"lizi","示例":"shili","教程":"jiaocheng","指南":"zhinan","手册":"shouce","说明":"shuoming","规则":"guize","规范":"guifan","标准":"biaozhun","要求":"yaoqiu","约束":"yueshu","限制":"xianzhi","边界":"bianjie","范围":"fanwei","作用域":"zuoyongyu","生命周期":"shengmingzhouqi","迭代":"diedai","版本":"banben","更新":"gengxin","升级":"shengji","回滚":"huigun","发布版":"fabuban","测试版":"ceshiban","正式版":"zhengshiban","预览版":"yulanban","灰度":"huidu","灰度发布":"huidufabu","推广":"tuiguang","上线":"shangxian","下线":"xiaxian","维护":"weihu","运维":"yunwei","运营":"yunying","销售":"xiaoshou","市场":"shichang","客户":"kehu","用户":"yonghu","案例":"anli","方案":"fangan","策略":"celue","预算":"yusuan","成本":"chengben","收入":"shouru","利润":"lirun","支出":"zhichu","资产":"zichan","负债":"fuzhai","现金流":"xianjinliu","估值":"guzhi","投资":"touzi","融资":"rongzi","上市":"shangshi","退市":"tuishi","并购":"binggou","重组":"zhongzu","破产":"pochan","清算":"qingsuan","法律":"falv","合规":"hegui","合同":"hetong","协议":"xieyi","条款":"tiaokuan","权利":"quanli","义务":"yiwu","责任":"zeren","风险":"fengxian","机遇":"jiyu","挑战":"tiaozhan","问题":"wenti","痛点":"tongdian","需求":"xuqiu","痛点需求":"tongdianxuqiu","功能需求":"gongnengxuqiu","非功能需求":"feigongnengxuqiu","性能需求":"xingnengxuqiu","可用性":"keyongxing","可靠性":"kekaoxing","安全性":"anquanxing","可维护性":"keweihuxing","可扩展性":"kkuozhanxing","兼容性":"jianrongxing","国际化":"guojihua","本地化":"bendihua","无障碍":"wuzhangai","高可用":"gaokeyong","高并发":"gaobingfa","高吞吐":"gaotuntuo","低延迟":"diyanchi","实时":"shishi","离线":"lixian","在线":"zaixian","远程":"yuancheng","本地":"bendi","服务器":"fuwuqi","客户端":"kehuduan","代理":"daili","网关":"wangguan","负载均衡":"fuzaijunheng","缓存":"huancun","消息队列":"xiaoxiduilie","数据库":"shujuku","分库分表":"fenkufenbiao","读写分离":"duxiefenli","主从复制":"zhucongfuzhi","备份恢复":"beifenhuifu","监控":"jiankong","日志":"rizhi","告警":"gaojing","链路追踪":"lianzhuizong","故障":"guzhang","容灾":"rongzai","灾备":"zaibei","多活":"duohuo","双活":"shuanghuo","三地":"sandi","异地":"yidi","跨境":"kuajing","跨域":"kuayu","跨平台":"kuapingtai","跨语言":"kuayuyan","跨终端":"kuazhongduan","响应式":"xiangyingshi","自适应":"zishiying","弹性":"tanxing","扩容":"kuorong","缩容":"suorong","限流":"xianliu","降级":"jiangji","熔断":"rongduan","重试":"chongshi","兜底":"doudi","回滚":"huigun","补偿":"buchang","幂等":"mideng","事务":"shiwu","隔离":"geli","沙箱":"shaxiang","安全":"anquan","加密":"jiami","解密":"jiemi","签名":"qianming","验签":"yanqian","认证":"renzheng","授权":"shouquan","鉴权":"jianquan","token":"token","jwt":"jwt","session":"session","cookie":"cookie","单点登录":"diandandenglu","多因子认证":"duoyinzirenzheng","动态口令":"dongtaikouling","生物识别":"shengwushibie","人脸识别":"renlianshibie","指纹":"zhiwen","虹膜":"hongmo","声纹":"shengwen","手势":"shoushi","行为识别":"xingweishibie","风险识别":"fengxianshibie","风控":"fengkong","反欺诈":"fangqizha","反洗钱":"fangxiqian","反作弊":"fangzuobi","反爬虫":"fanpachong","验证码":"yanzhengma","滑块":"huakuai","拼图":"pintu","短信":"duanxin","邮件":"youjian","推送":"tuisong","站内信":"zhhanneixin","广告":"guanggao","横幅":"hengfu","弹窗":"danchuang","浮窗":"fuchuang","推送":"tuisong","横幅":"hengfu","通栏":"tonglan","侧边栏":"cebianlan","页脚":"yejiao","页头":"yetou","面包屑":"mianbaoxie","分页":"fanye","无限滚动":"wuxiangundong","虚拟列表":"xuniliebiao","懒加载":"lanjiazai","预加载":"yujiazai","骨架屏":"gujiaoping","闪屏":"shanping","启动页":"qidongye","引导页":"yindaoye","新手":"xinshou","教学":"jiaoxue","教程":"jiaocheng","帮助":"bangz","反馈":"fankui","评价":"pingjia","评分":"pingfen","星级":"xingji","点赞":"dianzan","收藏":"shoucang","分享":"fenxiang","投诉":"tousu","举报":"jubao","屏蔽":"pingbi","拉黑":"lahei","禁言":"jinyan","封号":"fenghao","解封":"jiefeng","申诉":"shensu","客服":"kefu","工单":"gongdan","客服系统":"kefuxitong","支持":"zhichi","运维":"yunwei","运营":"yunying","商务":"shangwu","销售":"xiaoshou","市场":"shichang","品牌":"pinpai","推广":"tuiguang","公关":"gongguan","媒体":"meiti","公关媒体":"gongguanmeiti","媒介":"meijie","渠道":"qudao","代理":"daili","分销":"fenxiao","加盟":"jiameng","直营":"zhiying","加盟商":"jiamengshang","代理商":"dailishang","渠道商":"qudaoshang","合作伙伴":"hezuohuoban","战略合作":"zhanluehezuo","框架协议":"kuangjiaxieyi","备忘录":"beiwanlu","意向书":"yixiangshu","合同":"hetong","正式合同":"zhengshihetong","电子合同":"dianzihetong","纸质合同":"zhizhihetong","签约":"qianyue","续约":"xuyue","解约":"jieyue","终止":"zhongzhi","解除":"jiechu","解除合同":"jiechuhetong","违约":"weiyue","违约金":"weiyuejin","赔偿":"peichang","补偿":"buchang","诉讼":"susong","仲裁":"zhongcai","调解":"tiaoji","和解":"hejie","判决":"panjue","裁定":"caiding","执行":"zhixing","强制执行":"qiangzhizhixing","财产保全":"caichanbaoquan","证据":"zhengju","证人":"zhengren","鉴定":"jianding","审计":"shenji","税务":"shuiwu","发票":"fapiao","收据":"shouju","报销":"baoxiao","付款":"fukuan","收款":"shoukuan","转账":"zhuanzhang","汇款":"huikuan","承兑":"chengdui","托收":"tuoshou","信用证":"xinyongzheng","保函":"baohan","担保":"danbao","抵押":"diya","质押":"zhiya","留置":"liuzhi","优先":"youxian","受偿":"shouchang","抵销":"dixiao","提存":"ticun","破产":"pochan","重整":"chongzheng","和解":"hejie","清算":"qingsuan","债权":"zhaiquan","债务":"zhaiwu","应收":"yingshou","应付":"yingfu","预收":"yushou","预付":"yufu","暂收":"zanshou","暂付":"zanfu","代收":"daishou","代付":"daifu","承付":"chengfu","托收":"tuoshou","托付":"tuofu","委托":"weituo","代理":"daili","居间":"jujian","行纪":"xingji","信托":"xintuo","基金":"jijin","理财":"licai","理财":"licai","投资":"touzi","理财投资":"licaitouzi","理财管理":"licaiguanli","私人银行":"sirenyinhang","贵宾":"guibin","黑卡":"heika","白金卡":"baijinka","金卡":"jinka","普卡":"puka","信用卡":"xinyongka","借记卡":"jijika","储蓄卡":"chuxuka","工资卡":"gongzika","社保卡":"shebaoka","医保卡":"yibaoka","市民卡":"shiminka","公交卡":"gongjiaoka","校园卡":"xiaoyuanka","饭卡":"fanka","门禁卡":"menjinka","会员卡":"huiyuanka","积分卡":"jifenka","储值卡":"chuzhika","年卡":"nianka","季卡":"jika","月卡":"yueka","次卡":"cika","体验卡":"tiyanka","试用卡":"shiyongka","vip卡":"vipka","金卡":"jinka","钻石卡":"zuanshika","至尊卡":"zhizunka","尊享卡":"zunxiangka","非凡卡":"feifanka","先锋卡":"xianfengka","领航卡":"linghangka","旗舰卡":"qijianka","荣耀卡":"rongyaoka","钻石":"zuanshi","翡翠":"feicui","黄金":"huangjin","白银":"baiyin","黑曜石":"heiyaoshi","红宝石":"hongbaoshi","蓝宝石":"lanbaoshi","绿松石":"lusongshi","玛瑙":"manao","水晶":"shuijing","珍珠":"zhenzhu","翡翠玉":"feicuiyu","和田玉":"hetianyu","岫岩玉":"xiuyanyu","独山玉":"dushanyu","蓝田玉":"lantianyu","岫玉":"xiuyu","黄龙玉":"huanglongyu","金丝玉":"jinsiyu","金绞蜜":"jinmiaomi","琥珀":"hupo","蜜蜡":"mila","珊瑚":"shanhu","砗磲":"chequ","玳瑁":"daimao","象牙":"xiangya","犀角":"xijiao","羚羊角":"lingyangjiao","麝香":"shexiang","鹿茸":"lurong","燕窝":"yanwo","鱼翅":"yuchi","鲍鱼":"baoyu","海参":"haishen","鱼胶":"yujiao","鱼肚":"yudu","鱼唇":"yuchun","鱼鳔":"yubiao","鱼骨":"yugu","鱼鳞":"yulin","鱼皮":"yupi","鱼头":"yutou","鱼尾":"yuwei","鱼子":"yuzi","鱼籽":"yuzi","鱼苗":"yumiao","鱼种":"yuzhong","鱼塘":"yutang","鱼钩":"yugou","鱼竿":"yugan","鱼线":"yuxian","鱼饵":"yuer","鱼漂":"yupiao","鱼护":"yuhu","鱼笼":"yulong","鱼网":"yuwang","鱼叉":"yucha","鱼雷":"yulei","鱼雷艇":"yuleiting","鱼雷机":"yuleiji","鱼雷弹":"yuleidan","鱼雷发射管":"yuleifasheguan","鱼雷发射装置":"yuleifashezhizhi","鱼雷":"yulei"};

// 容错补全：unicode block 范围估算（极简）
function toPinyin(name) {
  if (!name) return '';
  let out = '';
  let i = 0;
  while (i < name.length) {
    const ch = name[i];
    const code = ch.charCodeAt(0);
    // 英文/数字/连字符/空格 → 小写保留
    if (/[a-zA-Z0-9\-_\s]/.test(ch)) {
      out += ch.toLowerCase();
      i++;
      continue;
    }
    // 中文：贪心尝试 4/3/2/1 字长词匹配
    let matched = false;
    for (let len = 4; len >= 1; len--) {
      const sub = name.substr(i, len);
      // 全是中文才尝试匹配
      if (/^[\u4E00-\u9FFF]+$/.test(sub) && PY[sub]) {
        out += PY[sub];
        i += len;
        matched = true;
        break;
      }
    }
    if (!matched) {
      // 没匹配到：保留原字
      out += ch;
      i++;
    }
  }
  return out.replace(/\s+/g, '');
}

// ===== 主流程 =====
const boardFile = app.vault.getAbstractFileByPath(BOARD_PATH);
if (!boardFile) {
  dv.paragraph(`❌ **找不到 board 文件** \`${BOARD_PATH}\``);
  return;
}

const boardContent = await app.vault.read(boardFile);

// 解析 board 中的所有 - [ ] [[...]] 卡片行，按 lane 分组
const lines = boardContent.split('\n');
const lanes = {};
let currentLane = '_pre';
for (let i = 0; i < lines.length; i++) {
  const line = lines[i];
  const lm = line.match(/^##\s+(.+)$/);
  if (lm) {
    currentLane = lm[1].trim();
    if (!lanes[currentLane]) lanes[currentLane] = [];
    continue;
  }
  const m = line.match(/^[-\s]*\[[xX\s]\]\s+\[\[([^\]]+)\]\]/);
  if (m && lanes[currentLane]) {
    const linkText = m[1];
    let path = linkText;
    let display = null;
    if (linkText.includes('|')) {
      [path, display] = linkText.split('|').map(s => s.trim());
    }
    path = path.trim();
    // 兼容 board 里写成 [[path/]] 或 [[path/|alias]]（带 .md 后缀）的格式
    if (path.endsWith('.md')) path = path.slice(0, -3);
    path = path + '.md';
    // 没有路径前缀（裸 [[名称]]）就放在 Cards/ 下
    if (!path.includes('/')) path = CARD_DIR.split('/').slice(-2).join('/') + '/' + path;
    lanes[currentLane].push({
      idx: i,
      line: line,
      path: path,
      display: display || path.split('/').pop().replace(/\.md$/, ''),
    });
  }
}

const tplFile = app.vault.getAbstractFileByPath(TEMPLATE_PATH);
if (!tplFile) {
  dv.paragraph(`❌ **找不到模板文件** \`${TEMPLATE_PATH}\``);
  return;
}
const tplContent = await app.vault.read(tplFile);

// 总览
let missing = 0, broken = 0, ok = 0;
for (const lane in lanes) {
  for (const c of lanes[lane]) {
    const f = app.vault.getAbstractFileByPath(c.path);
    if (!f) { missing++; continue; }
    try {
      const ct = await app.vault.read(f);
      if (ct.length < 200) broken++;
      else ok++;
    } catch (e) { broken++; }
  }
}

// ===== 渲染面板 =====
const summary = dv.el('div', '', { cls: 'pm-cm-summary' });
summary.style.cssText = 'padding:8px;margin-bottom:12px;border:1px solid var(--background-modifier-border);border-radius:6px;background:var(--background-secondary);';
summary.appendChild(dv.el('strong', `📊 卡片总览：${ok} OK / ${missing} 缺失 / ${broken} 损坏`));
summary.appendChild(dv.el('br'));
summary.appendChild(dv.el('small', '点击"生成"按钮新建模板文件；点击"重建"按钮覆盖损坏/空文件。', { attr: { style: 'color:var(--text-muted);' } }));

// 工具栏：一键生成所有缺失
const toolbar = dv.el('div', '', { cls: 'pm-cm-toolbar' });
toolbar.style.cssText = 'margin-bottom:12px;';
const btnAll = dv.el('button', '⚡ 一键生成所有缺失卡片');
btnAll.style.cssText = 'background:var(--interactive-accent);color:var(--text-on-accent);border:none;border-radius:6px;padding:8px 14px;cursor:pointer;font-weight:bold;';
btnAll.onclick = async () => {
  btnAll.disabled = true;
  btnAll.textContent = '⏳ 生成中…';
  let made = 0, failed = 0;
  for (const lane in lanes) {
    for (const c of lanes[lane]) {
      const f = app.vault.getAbstractFileByPath(c.path);
      if (f) continue;
      try {
        const title = c.path.split('/').pop().replace(/\.md$/, '');
        const ymd = (() => { const d = new Date(); return d.getFullYear() + '-' + String(d.getMonth()+1).padStart(2,'0') + '-' + String(d.getDate()).padStart(2,'0'); })();
        const pinyin = toPinyin(title);
        const expanded = tplContent
          .replace(/\{\{title\}\}/g, title)
          .replace(/\{\{title_pinyin\}\}/g, pinyin)
          .replace(/\{\{date\}\}/g, ymd);
        await app.vault.create(c.path, expanded);
        console.log('[PM-CM] CREATE ' + c.path + ' (pinyin=' + pinyin + ')');
        made++;
      } catch (e) {
        console.error('[PM-CM] FAIL ' + c.path, e);
        failed++;
      }
    }
  }
  btnAll.textContent = `✅ 完成：新建 ${made}，失败 ${failed}`;
  dv.refresh();
};
toolbar.appendChild(btnAll);
const btnRebuildAll = dv.el('button', '🔧 一键重建所有损坏卡片');
btnRebuildAll.style.cssText = 'background:var(--background-modifier-hover);color:var(--text-normal);border:1px solid var(--background-modifier-border);border-radius:6px;padding:8px 14px;cursor:pointer;margin-left:8px;';
btnRebuildAll.onclick = async () => {
  btnRebuildAll.disabled = true;
  btnRebuildAll.textContent = '⏳ 重建中…';
  let made = 0, skipped = 0;
  for (const lane in lanes) {
    for (const c of lanes[lane]) {
      const f = app.vault.getAbstractFileByPath(c.path);
      if (!f) { skipped++; continue; }
      try {
        const ct = await app.vault.read(f);
        if (ct.length >= 200) { skipped++; continue; }
        const title = c.path.split('/').pop().replace(/\.md$/, '');
        const ymd = (() => { const d = new Date(); return d.getFullYear() + '-' + String(d.getMonth()+1).padStart(2,'0') + '-' + String(d.getDate()).padStart(2,'0'); })();
        const pinyin = toPinyin(title);
        const expanded = tplContent
          .replace(/\{\{title\}\}/g, title)
          .replace(/\{\{title_pinyin\}\}/g, pinyin)
          .replace(/\{\{date\}\}/g, ymd);
        await app.vault.modify(f, expanded);
        console.log('[PM-CM] REBUILD ' + c.path);
        made++;
      } catch (e) {
        console.error('[PM-CM] FAIL ' + c.path, e);
      }
    }
  }
  btnRebuildAll.textContent = `✅ 完成：重建 ${made}，跳过 ${skipped}`;
  dv.refresh();
};
toolbar.appendChild(btnRebuildAll);

// 注入样式
const style = dv.el('style', '');
style.textContent = `
  .pm-cm-lane { margin: 12px 0 6px 0; font-weight: 600; color: var(--text-accent); }
  .pm-cm-row { display: flex; align-items: center; gap: 8px; padding: 4px 0; border-bottom: 1px solid var(--background-modifier-border); }
  .pm-cm-status { width: 60px; flex-shrink: 0; font-family: monospace; }
  .pm-cm-status.ok { color: var(--text-success); }
  .pm-cm-status.missing { color: var(--text-error); }
  .pm-cm-status.broken { color: var(--text-warning); }
  .pm-cm-name { flex: 1; min-width: 0; overflow: hidden; text-overflow: ellipsis; white-space: nowrap; font-family: var(--font-monospace); font-size: 13px; color: var(--text-muted); }
  .pm-cm-btn { background: var(--interactive-accent); color: var(--text-on-accent); border: none; border-radius: 4px; padding: 4px 10px; cursor: pointer; font-size: 12px; }
  .pm-cm-btn:hover { background: var(--interactive-accent-hover); }
  .pm-cm-btn.rebuild { background: var(--background-modifier-hover); color: var(--text-normal); border: 1px solid var(--background-modifier-border); }
`;

// 渲染每个 lane
for (const lane in lanes) {
  if (lanes[lane].length === 0) continue;
  dv.el('div', lane, { cls: 'pm-cm-lane' });
  for (const c of lanes[lane]) {
    const row = dv.el('div', '', { cls: 'pm-cm-row' });
    const f = app.vault.getAbstractFileByPath(c.path);
    let status = 'ok', statusText = '✅ OK';
    let needAction = false, action = 'rebuild';
    let sizeInfo = '';
    if (!f) { status = 'missing'; statusText = '❌ 缺失'; needAction = true; action = 'create'; }
    else {
      const ct = await app.vault.read(f);
      sizeInfo = ` (${ct.length} chars)`;
      if (ct.length < 200) { status = 'broken'; statusText = '⚠️ 损坏'; needAction = true; action = 'rebuild'; }
    }
    const stSpan = dv.el('span', statusText, { cls: 'pm-cm-status ' + status });
    row.appendChild(stSpan);
    const nameSpan = dv.el('span', c.display + sizeInfo, { cls: 'pm-cm-name', attr: { title: c.path } });
    row.appendChild(nameSpan);
    if (needAction) {
      const btn = dv.el('button', action === 'create' ? '⚡ 生成' : '🔧 重建', { cls: 'pm-cm-btn' + (action === 'rebuild' ? ' rebuild' : '') });
      btn.onclick = async () => {
        btn.disabled = true;
        btn.textContent = '⏳';
        try {
          const title = c.path.split('/').pop().replace(/\.md$/, '');
          const ymd = (() => { const d = new Date(); return d.getFullYear() + '-' + String(d.getMonth()+1).padStart(2,'0') + '-' + String(d.getDate()).padStart(2,'0'); })();
          const pinyin = toPinyin(title);
          const expanded = tplContent
            .replace(/\{\{title\}\}/g, title)
            .replace(/\{\{title_pinyin\}\}/g, pinyin)
            .replace(/\{\{date\}\}/g, ymd);
          if (action === 'create') {
            await app.vault.create(c.path, expanded);
            console.log('[PM-CM] CREATE ' + c.path + ' pinyin=' + pinyin);
          } else {
            await app.vault.modify(f, expanded);
            console.log('[PM-CM] REBUILD ' + c.path + ' pinyin=' + pinyin);
          }
          btn.textContent = '✅';
          dv.refresh();
        } catch (e) {
          console.error('[PM-CM] FAIL ' + c.path, e);
          btn.textContent = '❌';
          btn.disabled = false;
        }
      };
      row.appendChild(btn);
    }
    dv.el('div', '', { attr: { style: 'display:contents' } }); // placeholder
  }
}
```

---

## 为什么这个比 Kanban "New note from card" 可靠

1. **不走 Kanban 内部**：用 Obsidian 原生 `app.vault.create / modify`，Kanban 出问题完全不影响
2. **不走任何 main.js 补丁**：DataviewJS 是 Obsidian 内置 JS 沙箱，每次刷新视图都重新执行
3. **可见可点**：每个卡片都有按钮，按钮 onclick 直接调 API，不会被默默吞掉
4. **带日志**：Console 里 `Ctrl+Shift+I` 能看到 `[PM-CM] CREATE / REBUILD / FAIL` 的全部操作
5. **一键生成**：按钮旁边"⚡ 一键生成所有缺失卡片"，加新项目后一键全建

## 使用步骤

1. 加新卡片：在 board 里点 `+` 加任意名字（比如"测试3"）
2. 打开 `Views/PM Cards Manager` 这个文件
3. 看到红色"❌ 缺失"行 → 点"⚡ 生成"
4. 切回 `Cards/测试3.md` → 完整模板已生成

---

*实现版本: PM-CM v1 / 2026-09-12 / 完全独立于 Kanban main.js*