# Basic

```
/**
 * 1.双击显示当前
 * 2.单击当前显示全部
 * 3.单击某一个显隐切换
 *
 * 实现思路：
 * 对比第一次和第二次的时间;
 * 只有当curItem一样时才进行对比;
 */

const handleLineLegendChange = (() => {
  let isAgain = false; // 第二次点击标识
  let count = 0; // 计数（1 / 2）
  let lastTime = new Date().getTime(); // 上一次的时间
  let curItem = null; // 当前点击的item
  return (event, setOption, instance) => {
    const { name: legend, selected } = event;
    const curTime = new Date().getTime();
    if (curItem && curItem !== legend) {
      if (count > 1) {
        count = 0;
      }
      curItem = legend;
      isAgain = false;
      lastTime = new Date().getTime();
      return;
    }
    count = count + 1;

    if (count === 1) {
      // count2=>count1的情况
      if (curTime - lastTime <= 300) {
        for (const key in selected) {
          if (Object.prototype.hasOwnProperty.call(selected, key)) {
            if (key === legend) {
              instance.eChart.dispatchAction({ type: 'legendSelect', name: key });
            } else {
              instance.eChart.dispatchAction({ type: 'legendUnSelect', name: key });
            }
          }
        }
        isAgain = true;
        curItem = legend;
        count = 0;
      }
      curItem = legend;
      lastTime = curTime;
      if (!selected[legend] && isAgain) {
        instance.eChart.dispatchAction({
          type: 'legendAllSelect',
        });
        isAgain = false;
        count = 0;
        curItem = null;
      }
    }
    if (count === 2) {
      // count1=>count2 的情况
      if (curTime - lastTime <= 300) {
        for (const key in selected) {
          if (Object.prototype.hasOwnProperty.call(selected, key)) {
            if (key === legend) {
              instance.eChart.dispatchAction({ type: 'legendSelect', name: key });
            } else {
              instance.eChart.dispatchAction({ type: 'legendUnSelect', name: key });
            }
          }
        }
        isAgain = true;
        curItem = legend;
      }
      lastTime = new Date().getTime(); // count2=>count1
      count = 0;
    }
  };
})();

```