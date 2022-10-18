# Slither Analyzer Result

![Screenshot 2022-10-17 152444](https://user-images.githubusercontent.com/48362877/196295502-eaf68adf-4644-49c7-b741-5989b84acd49.png)

![image](https://user-images.githubusercontent.com/48362877/196295589-5c2bef66-c61e-4ea0-9b65-0bf19f0686eb.png)

Compilation warnings/errors on ./BulkSender.sol:
./BulkSender.sol:75:9: Warning: Invoking events without "emit" prefix is deprecated.
        Transfer(msg.sender, _to, _value);
        ^-------------------------------^
./BulkSender.sol:95:9: Warning: Invoking events without "emit" prefix is deprecated.
        Transfer(_from, _to, _value);
        ^--------------------------^
./BulkSender.sol:101:9: Warning: Invoking events without "emit" prefix is deprecated.
        Approval(msg.sender, _spender, _value);
        ^------------------------------------^


StandardToken (BulkSender.sol#88-107) has incorrect ERC20 function interface:ERC20.transferFrom(address,address,uint256) (BulkSender.sol#57)
StandardToken (BulkSender.sol#88-107) has incorrect ERC20 function interface:ERC20.approve(address,uint256) (BulkSender.sol#58)
StandardToken (BulkSender.sol#88-107) has incorrect ERC20 function interface:ERC20Basic.transfer(address,uint256) (BulkSender.sol#51)
StandardToken (BulkSender.sol#88-107) has incorrect ERC20 function interface:BasicToken.transfer(address,uint256) (BulkSender.sol#72-76)
StandardToken (BulkSender.sol#88-107) has incorrect ERC20 function interface:StandardToken.transferFrom(address,address,uint256) (BulkSender.sol#91-96)
StandardToken (BulkSender.sol#88-107) has incorrect ERC20 function interface:StandardToken.approve(address,uint256) (BulkSender.sol#98-102)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-erc20-interface

Ownable.transferOwnership(address) (BulkSender.sol#125-129) should emit an event for: 
        - owner = newOwner (BulkSender.sol#127) 
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#missing-events-access-control

BulkSender.setVIPFee(uint256) (BulkSender.sol#222-224) should emit an event for: 
        - VIPFee = _fee (BulkSender.sol#223) 
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#missing-events-arithmetic

Reentrancy in BulkSender.getBalance(address) (BulkSender.sol#153-163):
        External calls:
        - balance = token.balanceOf(this) (BulkSender.sol#160)
        - token.transfer(_receiverAddress,balance) (BulkSender.sol#161)
        Event emitted after the call(s):
        - LogGetToken(_tokenAddress,_receiverAddress,balance) (BulkSender.sol#162)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#reentrancy-vulnerabilities-3

SafeMath.div(uint256,uint256) (BulkSender.sol#14-19) is never used and should be removed
SafeMath.max256(uint256,uint256) (BulkSender.sol#35-37) is never used and should be removed
SafeMath.max64(uint64,uint64) (BulkSender.sol#29-31) is never used and should be removed
SafeMath.min256(uint256,uint256) (BulkSender.sol#38-40) is never used and should be removed
SafeMath.min64(uint64,uint64) (BulkSender.sol#32-34) is never used and should be removed
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#dead-code

Pragma version^0.4.0 (BulkSender.sol#1) allows old versions
solc-0.4.21 is not recommended for deployment
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#incorrect-versions-of-solidity

Parameter BasicToken.transfer(address,uint256)._to (BulkSender.sol#72) is not in mixedCase
Parameter BasicToken.transfer(address,uint256)._value (BulkSender.sol#72) is not in mixedCase
Parameter BasicToken.balanceOf(address)._owner (BulkSender.sol#78) is not in mixedCase
Parameter StandardToken.transferFrom(address,address,uint256)._from (BulkSender.sol#91) is not in mixedCase
Parameter StandardToken.transferFrom(address,address,uint256)._to (BulkSender.sol#91) is not in mixedCase
Parameter StandardToken.transferFrom(address,address,uint256)._value (BulkSender.sol#91) is not in mixedCase
Parameter StandardToken.approve(address,uint256)._spender (BulkSender.sol#98) is not in mixedCase
Parameter StandardToken.approve(address,uint256)._value (BulkSender.sol#98) is not in mixedCase
Parameter StandardToken.allowance(address,address)._owner (BulkSender.sol#104) is not in mixedCase
Parameter StandardToken.allowance(address,address)._spender (BulkSender.sol#104) is not in mixedCase
Parameter BulkSender.getBalance(address)._tokenAddress (BulkSender.sol#153) is not in mixedCase
Parameter BulkSender.addToVIPList(address[])._vipList (BulkSender.sol#178) is not in mixedCase
Parameter BulkSender.removeFromVIPList(address[])._vipList (BulkSender.sol#187) is not in mixedCase
Parameter BulkSender.isVIP(address)._addr (BulkSender.sol#196) is not in mixedCase
Parameter BulkSender.setReceiverAddress(address)._addr (BulkSender.sol#203) is not in mixedCase
Parameter BulkSender.setVIPFee(uint256)._fee (BulkSender.sol#222) is not in mixedCase
Parameter BulkSender.setTxFee(uint256)._fee (BulkSender.sol#229) is not in mixedCase
Parameter BulkSender.ethSendSameValue(address[],uint256)._to (BulkSender.sol#233) is not in mixedCase
Parameter BulkSender.ethSendSameValue(address[],uint256)._value (BulkSender.sol#233) is not in mixedCase
Parameter BulkSender.ethSendDifferentValue(address[],uint256[])._to (BulkSender.sol#254) is not in mixedCase
Parameter BulkSender.ethSendDifferentValue(address[],uint256[])._value (BulkSender.sol#254) is not in mixedCase
Parameter BulkSender.coinSendSameValue(address,address[],uint256)._tokenAddress (BulkSender.sol#277) is not in mixedCase
Parameter BulkSender.coinSendSameValue(address,address[],uint256)._to (BulkSender.sol#277) is not in mixedCase
Parameter BulkSender.coinSendSameValue(address,address[],uint256)._value (BulkSender.sol#277) is not in mixedCase
Parameter BulkSender.coinSendDifferentValue(address,address[],uint256[])._tokenAddress (BulkSender.sol#298) is not in mixedCase
Parameter BulkSender.coinSendDifferentValue(address,address[],uint256[])._to (BulkSender.sol#298) is not in mixedCase
Parameter BulkSender.coinSendDifferentValue(address,address[],uint256[])._value (BulkSender.sol#298) is not in mixedCase
Parameter BulkSender.sendEth(address[],uint256)._to (BulkSender.sol#322) is not in mixedCase
Parameter BulkSender.sendEth(address[],uint256)._value (BulkSender.sol#322) is not in mixedCase
Parameter BulkSender.bulksend(address[],uint256[])._to (BulkSender.sol#329) is not in mixedCase
Parameter BulkSender.bulksend(address[],uint256[])._value (BulkSender.sol#329) is not in mixedCase
Parameter BulkSender.bulkSendETHWithDifferentValue(address[],uint256[])._to (BulkSender.sol#337) is not in mixedCase
Parameter BulkSender.bulkSendETHWithDifferentValue(address[],uint256[])._value (BulkSender.sol#337) is not in mixedCase
Parameter BulkSender.bulkSendETHWithSameValue(address[],uint256)._to (BulkSender.sol#345) is not in mixedCase
Parameter BulkSender.bulkSendETHWithSameValue(address[],uint256)._value (BulkSender.sol#345) is not in mixedCase
Parameter BulkSender.bulkSendCoinWithSameValue(address,address[],uint256)._tokenAddress (BulkSender.sol#353) is not in mixedCase
Parameter BulkSender.bulkSendCoinWithSameValue(address,address[],uint256)._to (BulkSender.sol#353) is not in mixedCase
Parameter BulkSender.bulkSendCoinWithSameValue(address,address[],uint256)._value (BulkSender.sol#353) is not in mixedCase
Parameter BulkSender.bulkSendCoinWithDifferentValue(address,address[],uint256[])._tokenAddress (BulkSender.sol#360) is not in mixedCase
Parameter BulkSender.bulkSendCoinWithDifferentValue(address,address[],uint256[])._to (BulkSender.sol#360) is not in mixedCase
Parameter BulkSender.bulkSendCoinWithDifferentValue(address,address[],uint256[])._value (BulkSender.sol#360) is not in mixedCase
Parameter BulkSender.bulksendToken(address,address[],uint256[])._tokenAddress (BulkSender.sol#367) is not in mixedCase
Parameter BulkSender.bulksendToken(address,address[],uint256[])._to (BulkSender.sol#367) is not in mixedCase
Parameter BulkSender.bulksendToken(address,address[],uint256[])._value (BulkSender.sol#367) is not in mixedCase
Parameter BulkSender.drop(address,address[],uint256)._tokenAddress (BulkSender.sol#373) is not in mixedCase
Parameter BulkSender.drop(address,address[],uint256)._to (BulkSender.sol#373) is not in mixedCase
Parameter BulkSender.drop(address,address[],uint256)._value (BulkSender.sol#373) is not in mixedCase
Variable BulkSender.VIPFee (BulkSender.sol#145) is not in mixedCase
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#conformance-to-solidity-naming-conventions

Reentrancy in BulkSender.ethSendDifferentValue(address[],uint256[]) (BulkSender.sol#254-275):
        External calls:
        - require(bool)(_to[i].send(_value[i])) (BulkSender.sol#271)
        Event emitted after the call(s):
        - LogTokenBulkSent(0x000000000000000000000000000000000000bEEF,msg.value) (BulkSender.sol#273)
Reentrancy in BulkSender.ethSendSameValue(address[],uint256) (BulkSender.sol#233-252):
        External calls:
        - require(bool)(_to[i].send(_value)) (BulkSender.sol#248)
        Event emitted after the call(s):
        - LogTokenBulkSent(0x000000000000000000000000000000000000bEEF,msg.value) (BulkSender.sol#251)
Reentrancy in BulkSender.registerVIP() (BulkSender.sol#168-173):
        External calls:
        - require(bool)(_receiverAddress.send(msg.value)) (BulkSender.sol#171)
        State variables written after the call(s):
        - vipList[msg.sender] = true (BulkSender.sol#172)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#reentrancy-vulnerabilities-4

ERC20Basic.totalSupply (BulkSender.sol#49) should be constant
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#state-variables-that-could-be-declared-constant

addToVIPList(address[]) should be declared external:
        - BulkSender.addToVIPList(address[]) (BulkSender.sol#178-182)
removeFromVIPList(address[]) should be declared external:
        - BulkSender.removeFromVIPList(address[]) (BulkSender.sol#187-191)
sendEth(address[],uint256) should be declared external:
        - BulkSender.sendEth(address[],uint256) (BulkSender.sol#322-324)
bulksend(address[],uint256[]) should be declared external:
        - BulkSender.bulksend(address[],uint256[]) (BulkSender.sol#329-331)
bulkSendETHWithDifferentValue(address[],uint256[]) should be declared external:
        - BulkSender.bulkSendETHWithDifferentValue(address[],uint256[]) (BulkSender.sol#337-339)
bulkSendETHWithSameValue(address[],uint256) should be declared external:
        - BulkSender.bulkSendETHWithSameValue(address[],uint256) (BulkSender.sol#345-347)
bulkSendCoinWithSameValue(address,address[],uint256) should be declared external:
        - BulkSender.bulkSendCoinWithSameValue(address,address[],uint256) (BulkSender.sol#353-355)
bulkSendCoinWithDifferentValue(address,address[],uint256[]) should be declared external:
        - BulkSender.bulkSendCoinWithDifferentValue(address,address[],uint256[]) (BulkSender.sol#360-362)
bulksendToken(address,address[],uint256[]) should be declared external:
        - BulkSender.bulksendToken(address,address[],uint256[]) (BulkSender.sol#367-369)
drop(address,address[],uint256) should be declared external:
        - BulkSender.drop(address,address[],uint256) (BulkSender.sol#373-375)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#public-function-that-could-be-declared-external
. analyzed (7 contracts with 81 detectors), 78 result(s) found
