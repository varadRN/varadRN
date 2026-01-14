# varadN
  
varad


varad nakhate




Full stack web devloper
#varad nakhate
#varad nakhate
#varad nakhate
# zenbook

#Macbook 14
#Apple
# Happy New Year
# 01/01/2026
# 02/01/2026
# Friday
# 03/01/2026
# Saturday
# Resume Ready ATS score - 87-88
# 04/01/2026
# Sunday
# 05/01/2026
# Monday
# 06/01/2026
# Tuesday
# 07/01/2026
# Wednesday
# 08/01/2026
# Thursday
# 09/01/2026
# Friday
# 10/01/2026
# Saturday
# 12/01/2026
# Monday
# 13/01/2026
# Tuesday
# 14/02/2026
# Wednesday





// frontend/src/nodes/BaseNode.js
import React from 'react';
import { Handle, Position } from 'reactflow';
import { useNodeId } from 'reactflow';
import styles from './BaseNode.module.css'; // Import the CSS module

export default function BaseNode({
data,
type,
label = type,
icon = null,
children,
customBodyComponent: CustomBodyComponent = null,
handleConfig = { inputs: [], outputs: [] },
className = '',
style = {}
}) {
const nodeId = useNodeId();

const renderHandles = (positions, handleType) => {
    if (!Array.isArray(positions)) return null;

    return positions.map((pos, index) => {
    const handleId = `${nodeId}-${handleType}-${index}`;
    const positionEnum = pos === 'left' ? Position.Left :
                        pos === 'right' ? Position.Right :
                        pos === 'top' ? Position.Top : Position.Bottom;

    return (
        <Handle
        key={handleId}
        type={handleType}
        position={positionEnum}
        id={handleId}
          className={styles['react-flow__handle']} // Apply handle styles
        />
    );
    });
};

return (
    <div className={`${styles.baseNode} ${className}`} style={style}> {/* Apply base node styles */}
    <div className={styles.nodeHeader}>
        {icon && <span className={styles.nodeIcon}>{icon}</span>}
        <strong>{label}</strong>
    </div>

    <div className={styles.nodeBody}>
        {CustomBodyComponent ? <CustomBodyComponent nodeId={nodeId} data={data} /> : children}
    </div>

    {renderHandles(handleConfig.inputs, 'target')}
    {renderHandles(handleConfig.outputs, 'source')}
    </div>
);
}
