
# react-native-multi-state-modal
[![npm version](https://badge.fury.io/js/react-native-multi-state-modal.svg)](https://badge.fury.io/js/react-native-multi-state-modal)


A simple and customisable react-native multi-state modal

## Features
- Customizable state by array of height
- Customizable speed during transition
- Draggable 

## Demo

<p align="center">
<img src="https://media.giphy.com/media/3oFzm2uDRXErwdspRm/giphy.gif" height="500" />
</p>

## Setup
Install it with: 

`npm install --save react-native-multi-state-modal` , or 

`yarn add react-native-multi-state-modal`.

## Usage

```javascript
import React, {Component} from 'react';
import {Dimensions, StyleSheet, Text, View, TouchableOpacity} from 'react-native';
import Modal from 'react-native-multi-state-modal'

const { width, height } = Dimensions.get('window');

type Props = {};
export default class App extends Component<Props> {
  constructor(props) {
		super(props);

		this.state = {
			stateIndex: 0,
			buttonText: 'Open modal'
		}
	}

	render() {

		let { stateIndex } = this.state;
		return (
			<View style={styles.container}>
				<View style={{flex: 1}} >
					<TouchableOpacity 
						style={styles.button}
						onPress={() => this.setState({stateIndex: stateIndex == 0? 1 : 0})}>
						<Text style={{color: 'white', fontSize: 20}}>{this.state.buttonText}</Text>
					</TouchableOpacity>
				</View>
				<Modal
					style={{backgroundColor: 'white'}}
					states={[0, height * 3 / 16, height * 447 / 640 ]}
					stateIndex={stateIndex}
					speed={300} 
					onIndexChange={(index) => this.setState({stateIndex: index})} >
					<View style={{flex: 1}}>
						<Text style={{color: 'black', fontSize: 20}}>Test content</Text>
					</View>
				</Modal>
			</View>
		);
	}
}

const styles = StyleSheet.create({
	container: {
		flex: 1,
		justifyContent: 'center',
		alignItems: 'center',
		backgroundColor: '#F5FCFF',
	},
	button: {
		paddingHorizontal: 12, 
		paddingVertical: 6, 
		backgroundColor: 'grey'
	}
});
```
For a more complex example take a look at the /example directory.
## props

| Name | Type| Default | Required | Description |
| --- | --- | --- | --- | --- |
| states | array | NA | Yes | Array oh height of each state in ascending order |
| stateIndex | number | NA | Yes | State index  |
| enableDrag | boolean | true | No | set it to true to enable drag  |
| speed | number | 300 | No | Speed during transition between states |
| onPress | func | null | No | if onPress is not null and enableDrag is false, this function will be triggered |
| onIndexChange | func | null | No | function that gives you the index after change  |
