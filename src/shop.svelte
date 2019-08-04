<script>
  let get = JSON.parse(localStorage.getItem("key"));
  console.log(get);
  let sum = 0;
  let checked = false;
  function add(ind) {//加
    get[ind].num++;
    sums();
  }
  function sub(ind) {//减
    if (get[ind].num > 1) {
      get[ind].num--;
    } else {
      get[ind].num = 1;
    }
    sums();
  }
  function sums() {//总价
    sum=0;
    get.forEach(item=>{
      if(item.flag){
        sum += item.num * item.price;
      }
    })
    // sum=get.reduce(function(a, b) {
    //   // console.log(b.flag)
    //   if(b.flag){
    //      return a + b.num * b.price;
    //   }
    // }, 0);
  }
  function btn(i) {//单选

    get[i].flag = !get[i].flag;
    let flag = get.every(item=>item.flag)
    if(flag){
      checked = true;
    }else{
      checked = false;
    }
    sums();
  }
  function allChecked(){//多选
    checked=!checked;
    get.map(item=>{
      item.flag = checked;
    });
    get = get;
    sums();
  }
</script>
<style>
  .list {
    width: 100%;
    display: flex;
  }
  .list input {
    width: 30px;
    height: 30px;
    line-height: 30px;
    margin: 50px 5px;
  }
  .list dl {
    display: flex;
    background: #eee;
    margin: 10px;
    text-align: center;
    align-items: center;
  }
  .list dl dt img {
    width: 120px;
  }
  .list dl dd {
    font-size: 14px;
    text-align: center;
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  .head {
    width: 100%;
    height: 50px;
    background: red;
    line-height: 50px;
    display: flex;
    justify-content: space-around;
    align-items: center;
    text-align: center;
    color: #fff;
  }
  .head input {
    width: 30px;
    height: 30px;
    line-height: 30px;
    border-radius: 100%;
    text-align: left;
  }
  .active {
    background: red;
  }
</style>

<div class="head">
  <input type="radio" on:click={allChecked} {checked}/>
  <h3>hans超级店铺</h3>
  <p>总价:{sum}</p>
</div>
{#each get as item, ind}
  <div class="list">
    <input
      on:click={() => {
        btn(ind);
      }}
      type="radio"
      checked={item.flag} />
    <dl>
      <dt>
        <img src={item.img} alt="" />
      </dt>
      <dd>
        <div>
          <span>{item.title}</span>
          <p>￥{item.price}</p>
        </div>
        <div class="methods">
          <span
            on:click={() => {
              sub(ind);
            }}>
            -
          </span>
          <span>{item.num}</span>
          <span
            on:click={() => {
              add(ind);
            }}>
            +
          </span>
        </div>

      </dd>
    </dl>

  </div>
{/each}
<div />
