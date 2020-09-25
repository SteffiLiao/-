# -
請求老哥高抬貴手幫助

pm25 = int(input())               # pm25 = pm2.5 濃度
temp = int(input())               # temp = 氣溫
dew = int(input())                # dew = 露點溫度
w = float(input())                # w = 赴約臨界值
w0 = 0.5

# wa = 空汙影響的赴約意願值
wa = float()
if pm25 <= 35:
    wa = w0 + 0.005*(100-pm25)
else:
    wa = w0 + 0.02*(45-pm25)

# wh = 相對溼度影響的赴約意願值
humi = 100 - 5*(temp-dew)         # humi = 相對濕度%
wh = float()
if humi <= 30:
    wh = (w0/60) * (110-humi)
else:
    wh = (w0/45) * (90-humi)

# 因空汙影響出遊意願調整項
if wa < 0:
    wa = 0
elif wa > 1:
    wa = 1
else:
    pass

# 因濕度影響出遊意願調整項
if wh < 0:
    wh = 0
elif wh > 1:
    wh = 1
else:
    pass

# 決定去的意願值（取低值）
if wa <= wh:
    intention_to_go = wa
else:
    intention_to_go = wh

# 告訴毛毛的話
if intention_to_go >= w:
    print('{:.2f}'.format(intention_to_go), "\nLet's go together")
else:
    print('{:.2f}'.format(intention_to_go), "\nI wouldn't go out with you.")
